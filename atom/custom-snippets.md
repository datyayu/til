To create your own snippets on atom, you can edit the file at `~/.atom/snippets.cson`.

The format for a new snippet is:

```coffee
'.source.js': # <-- Target files (here, i choose *.js)
  'My snippet': # <-- Snippet name
    'prefix': 'snip' # <-- Text you have to write to use the snippet.
    'body': ''' # <-- Snippet
      import React from 'react'
      import expect from 'expect'
      import { shallow } from 'enzyme'

      import { $1 } from './'

      describe('<$1 />', () => {
        it('should render', () => {
          const renderedComponent = shallow(
            <$1 />
          )
          expect(renderedComponent.is('div')).toEqual(true)
        })
      })
    '''
```

Where `$1` (or `$n`) is a value that will be prompted to enter when you use the snippet.


[Source](https://www.learnphoenix.io/#/phoenix-chat/snippets_and_aliases.md?_k=01wosz) 
