Director pattern
================

> Director({String})

reutrn a Director instance which named 'tab', if not existed, will create a new instance

+ ``$define``  define this director
    

    Director('hongru').$define(function () {
        // todo
        this.age = 23;
        this.say = ...
    });
    
    //or
    Director('test').$define({
        aa: ...,
        bb: ...
    });

    
can also use sub namespace such as:

    Director('hongru').$define('util', function () {
        ...
    });
    
    // or
    Director('hongru').$define('util', {
        ...
    });
    
    
+ ``$actor``  get one of his actor, if not existed, will create new; 

can also use ``$define`` to define a actor;

    Director('hongru').$actor('body').$define(function () {
        //todo
    });
    
actor has ``$focus`` method which can focus on an event he insterested in, subscribe a handler[fn] to this event.

    Director('hongru').$actor('body').$focus('onWinResize', function (dim) {
        //todo
        
    });
    
in actor's constructor, ``this.$director`` can get his director.

    
    
+ ``$notify`` notify his actors an event with msgs, his actor who ``$focus`` this event will activate the right handler

    Director('hongru').$notify('onWinResize', {width: 300, height: 200});
    
    
+ ``$wake`` director wake up, initialize the application. He will wake all his actors up, then run ``$act``.


    

    

    