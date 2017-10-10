Alarm
#####

A real time or astronomical alarm to trigger a one-off or repeating function. The event condition is set through the ``datetime`` property.

The alarm can be cancelled at any time with ``cancel()``.

Properties
**********

Alarm.datetime
==============

The DateTime object set as the alarm's event condition, or ``nil`` if none has been set. The DateTime object is part of the :doc:`../guide/controller-api`.

Alarm.active
============

True if the alarm will call the ``alarm_handler`` when the next event condition occurs; otherwise false.

Alarm.single_shot
=================

This property determines whether the alarm is single-shot. A single-shot alarm will call its ``alarm_handler`` only once; repeating alarms call their ``alarm_handler`` every time their event occurs.

An alarm where ``datetime`` is set to an absolute date (i.e. one with a month and year) will be inherently single shot and this ``single_shot`` property will have no effect.

Methods
*******

Alarm.new() -> Alarm
====================

Create a new alarm.

Alarm:cancel()
==============

Cancels the alarm. The ``alarm_handler`` will not be called next time the event condition is matched.

Alarm:resume()
==============

Reinstates the alarm after ``cancel()`` has been called or after a single-shot alarm has matched its event condition once. The ``alarm_handler`` will be called next time the event condition is matched.

Event handlers
**************

Alarm.alarm_handler
===================

The handler has the following signature:

.. code-block:: lua
   
   function(alarm)

The handler is called each time the alarm event condition is matched.
