# Lua Notify C API 
<!-- ---------------------------------------------------------------------------------------- -->

The *Notify C API* can be used to get asynchronous notifications from native code running 
in other threads, e.g. a GUI thread may get a notification interrupting the event loop for
processing result data from another thread, see [lpugl/example10.lua].

   * Lua objects implementing the *Notify C API* can receive asynchronous notifications.
   * Native C code invoking the *Notify C API* can send asynchronous notifications from any thread.

Lua objects implementing the *Notify C API* must
have an associated meta table entry *_capi_notify* delivered by
the C API function *notify_get_capi()* and the associated 
C API function *toNotifier()* must return a valid pointer for the given 
notifier object. For further documentation see [notify_capi.h](./notify_capi.h).

<!-- ---------------------------------------------------------------------------------------- -->

### Implementations:

   * [mtmsg] buffer objects are implementing the *Notify C API*. If notified, the buffer
     receives an empty message, see [mtmsg/example06.lua].

   * [mtstates] state objects are implementing the *Notify C API*. If notified, the state's
     callback function is invoked without arguments, see [mtstates/example06.lua].

   * [nocurses] implements the *Notify C API* to be interruptible while waiting
     for keyboard input,  see [nocurses/example03.lua].

   * [lpugl] world objects are implementing the *Notify C API* to be interruptible while 
     waiting for GUI events, see [lpugl/example10.lua].


### Invocations:

   * [mtmsg] buffer objects are sending notifications to a registered notifier object
     if a new message is added to the buffer, see [mtmsg/example06.lua] 
     or [lpugl/example10.lua].

<!-- ---------------------------------------------------------------------------------------- -->

[mtmsg]:                  https://github.com/osch/lua-mtmsg
[mtmsg/example06.lua]:    https://github.com/osch/lua-mtmsg/blob/master/examples/example06.lua

[mtstates]:               https://github.com/osch/lua-mtstates
[mtstates/example06.lua]: https://github.com/osch/lua-mtstates/blob/master/examples/example06.lua

[nocurses]:               https://github.com/osch/lua-nocurses
[nocurses/example03.lua]: https://github.com/osch/lua-nocurses/blob/master/examples/example03.lua

[lpugl]:                  https://github.com/osch/lua-lpugl
[lpugl/example10.lua]:    https://github.com/osch/lua-lpugl/blob/master/example/example10.lua


<!-- ---------------------------------------------------------------------------------------- -->

## License 

This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this
software, either in source code form or as a compiled binary, for any purpose,
commercial or non-commercial, and by any means.

<!-- ---------------------------------------------------------------------------------------- -->
