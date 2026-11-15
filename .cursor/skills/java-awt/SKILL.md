---
name: java-awt
description: >-
  Uses java.awt on the event dispatch thread. Use when editing AWT components,
  EventQueue, Window, Frame, Dialog, Graphics, or painting.
---

# java.awt

`java.awt.EventQueue` is the event dispatch thread. `EventQueue.invokeLater` runs code there. Component access and painting run on that thread. Guide: [Concurrency in Swing](https://docs.oracle.com/javase/tutorial/uiswing/concurrency/index.html).

Do not use AWT `Button`, `Label`, `TextField`, `TextArea`, `List`, or `Canvas` for plugin UI. Use Swing or the IntelliJ components in [docs/runtime.md](../../../docs/runtime.md).

`Window`, `Frame`, and `Dialog` are heavyweight peers. Prefer a `JComponent` that the platform places in a tool window or dialog. An existing `com.intellij` or `org.jetbrains` class, function, or constant wins over a new helper.

Draw with `Graphics` only from the paint path (`paint`, `update`, or Swing `paintComponent`). Do not keep a `Graphics` and draw with it later.
