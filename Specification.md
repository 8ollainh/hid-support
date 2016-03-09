# Introduction #

hid-support consists of a server that runs inside of SpringBoard or Lowtide. IPC is done via Mach Port RPC. The message ID is used to encode the desired action.


# Details #

It will provide the following HID support actions (with command id):

  * Text injection (0x01)
    * Data: UTF8 string

  * Key down/up (x02)
    * Assumption: hid-support OR iOS provides key repetition
    * Data: uint16\_t down flag
    * Data: uint32\_t key modifiers flag. OR of CMD (0x01), ALT (0x02)
    * Data: uint32\_t unicode of key. Enumeration of special keys to be defined

  * Remote control down/up (0x03):
    * Assumption: users e.g. sends down and up if she wants a single move left
    * Data: uint16\_t down flag
    * Data: uint32\_t enum of up/down/left/right/menu/select/play

  * Mouse pointer (0x04)
    * keep-alive:
      * enable pointers
    * relative movement
      * for mouse/trackpad driver
      * movement on screen depends on screen orientation
    * absolute position
      * for VNC
      * position is absolute to fixed screen geometry
    * Data: enum {keep-alive=1, absolute, relative} type
    * Data: int32 x,y
    * Data: uint16\_t mouse buttons down/up

  * Multitouch (0x05)
    * coordinates in screen geometry
    * Data: int32 number of touches, {(x,y)}`*`

  * Accelerometer (0x06)
    * Data: float x/y/z

  * Button up/down (0x07)

  * Assumption: users e.g. sends down and up if she wants a single move left
  * Data: uint16\_t down flag
  * Data: uint32\_t enum of e.g. HWHomeButton