---
name: javax-swing
description: >-
  Writes javax.swing UI on the event dispatch thread. Use when editing Swing
  components, layouts, listeners, JPanel, JButton, JLabel, JTextField, or other
  javax.swing types.
---

# javax.swing

Build and read Swing components only on the event dispatch thread. Schedule that work with `SwingUtilities.invokeLater`. `invokeAndWait` blocks the caller until the EDT finishes. Do not call it from the EDT.

Do not block the EDT with IO, sleep, or a long computation. Swing is not thread safe. Guide: [Concurrency in Swing](https://docs.oracle.com/javase/tutorial/uiswing/concurrency/index.html).

Use a layout manager (`BorderLayout`, `BoxLayout`, `GridBagLayout`). Do not use a null layout. Guide: [Using layout managers](https://docs.oracle.com/javase/tutorial/uiswing/layout/using.html).

Do not add a heavyweight AWT control (`java.awt.Button`, `TextField`, `TextArea`, `Label`, `List`, `Canvas`) to a `JComponent`. Mixing them breaks painting and events. Guide: [Mixing heavy and light components](https://docs.oracle.com/javase/tutorial/uiswing/components/mixing.html).

In this plugin, prefer the IntelliJ wrappers in [docs/runtime.md](../../../docs/runtime.md) (`JBLabel`, `JBPanel`, the Kotlin UI DSL) over raw Swing. An existing `com.intellij` or `org.jetbrains` class, function, or constant wins over a new helper.

Listeners run on the EDT. Hand long work to a background task instead of doing it inside the listener.
