On Django Rest Framework, if you want to get nested references populated, you can specify the depth to which you want to populate.

In example,
``` python
from rest_framework import serializers
from models import Artist

class ArtistsSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Artist
        fields = ('name', 'image', 'bio', 'albums', 'songs')
```

will generate something like
```json
  {
      "name": "Hanazawa Kana",
      "image": "http://localhost:8000/media/1455604239.89_0512bdc8-5ba3-475c-a57a-a6ea87baa8a0.jpg",
      "bio": "such a cute.",
      "albums": [
          "http://localhost:8000/api/albums/1/"
      ],
      "songs": [
          "http://localhost:8000/api/songs/1/"
      ]
  }
```

While when using `depth` you can get the references populated like this.

``` python
class ArtistsSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Artist
        depth = 1
        fields = ('name', 'image', 'bio', 'albums', 'songs')
```

``` json
  {
      "name": "Hanazawa Kana",
      "image": "http://localhost:8000/media/1455604239.89_0512bdc8-5ba3-475c-a57a-a6ea87baa8a0.jpg",
      "bio": "such a cute.",
      "albums": [
          {
              "url": "http://localhost:8000/api/albums/1/",
              "title": "Coupling Album",
              "image": "http://localhost:8000/media/1455611567.38_album_e2507dbc-d80e-4ecc-9c34-4bbe378842b5.jpg",
              "single_type": "Album",
              "artists": [
                  "http://localhost:8000/api/artists/4/"
              ]
          }
      ],
      "songs": [
          {
              "url": "http://localhost:8000/api/songs/1/",
              "number": 1,
              "title": "Timeless",
              "audio_file": "http://localhost:8000/media/1455614232_song_5683e95e-2911-4d75-87e9-8af6a65ed9c2.mp3",
              "album": "http://localhost:8000/api/albums/1/",
              "artists": [
                  "http://localhost:8000/api/artists/4/"
              ]
          }
      ]
  }
```

*NOTE:* You can go WAY deeper, but be aware that this may cause duplicates on the tree.

[Source](http://stackoverflow.com/questions/14573102/how-do-i-include-related-model-fields-using-django-rest-framework)
