## 'Spontaneous Node'

### A personal MEAN boilerplate
    
  This is where I merge up all my frontend solutions from various work/personal projects into one foundational template. When I find a nifty way of structuring/doing stuff, I'll dump it here so I can reuse it for next time.

  I may or may not turn it into a yeoman generator at some point.
    
#### Frontend 7th Symphony, composed by Wolfgang Gulpenstein
  - A meaty **gulpfile** that works alongside **skeleton structures** for...
  - **OOSCSS**
    - *SASS* preprocessor
    - *Normalize.css* by (@necolas v3.0.2)
    - *clrs.cc* (@mrmrs v2.0)
  - **AngularJS** & **Angular UI Router**

  NB: All outdoor-facing frontend assets distribute to `/assets/(styles|scripts|images|...)`

#### TODO: Backend Overture, by the massed phillharmonic Node/Sails orchestra
  - An optional skeleton for **Node.js** development utilising...
  - **Sails.js** 
  - **Swig** html rendering
    - Change 
  - **Passport.js** auth
  - **Orchestrate.io** data service (via sails-orchestra adapter)

### Universal find-in-file notation
I use this simple notation system in conjunction with a texteditor's find-in-file search function. The defined glyphs are used within comments, preferably at the start of new lines, and in most cases are followed by a concise accompanying note.

##### Glyphs v2.0:
```
  @@@ : NB      : Generic find-in-file prefix (for HTML, use <!--# -->)
  >>> : MEAT    : Add some meat to this dummy/skeleton codeblock
  +++ : BUILD   : Accompanying comment suggests a new feature
  ^^^ : REFACTOR: Neaten up, improve or rework the internals of this system
  VVV : HUNT    : Hunt out and remove all references/dependencies to this codeblock
  ??? : PONDER  : Reconsider the implementation/necessity of this codeblock
  >-< : SPLIT   : Pull this codeblock apart, into more manageable/reusable chunks
  !!! : KILL    : Fix this inconsistency / bug
```

### Style guide

#### SCSS
  - With inspiration from [BEM][BEM], [CSSGuidelin.es][CSSG] and [TitleCSS][TtlCSS]

```
    $class-color: #EEE;       // Define colours as variables. Always.
                              // Compactly format single-property classes
    * { box-sizing: border-box; }
  
    .Class {                  // Capitalise objects, treat as new Block()
                              // Order CSS properties as such
      display: block;         // 1. Positioning & Layout
      position: absolute;
      top: 0;
  
      width: 10%;             // 2. Box-model structure
         
      padding: 40px;          // 3. Non-structural style (assuming box-sizing)
      background: $class-color;
      border: 2px solid darken($class-color,20%);
  
      font: {                 // 4. Type
        size: 20px;
        family: 'Comic Sans', 'Windings', monospace;
      }
  
      &:before {              // 5. Content
        content: 'Kakaw';
      }
  
      &:hover {               // 6. Interaction
        cursor: pointer;  
        background: lighten($class-color,10%);
      }
    }
  
    .Subclass,                // Selectors on separate lines
    .SomeOtherSubclass {                 
                              // @(extend|include) at top of class
      @extend .Class;         // * Treat extended classes as OOP parent classes
      @include trait;         // * Treat included mixins as OOP traits
                              // Child elements defined below root properties
      &__semantic-child {     // * Utilise & to generate BEM-style selectors
                              // * Two options for modifiers:
        &.modifier.s {        // * 1. Reusable appended classes for modifiers
          /***/ 
        }
        &--unique-modifier {  // * 2. Optionally use unique BEM --modifiers
          /***/ 
        }
      }
    }
```

[CSSG]: http://cssguidelin.es/#bem-like-naming
[BEM]: http://www.integralist.co.uk/posts/maintainable-css-with-bem/
[TtlCSS]: http://www.sitepoint.com/title-css-simple-approach-css-class-naming/
