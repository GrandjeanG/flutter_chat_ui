# [Flyer Chat](https://flyer.chat) 💬

**Ship fast with a go-to chat SDK for Flutter.**

[![Pub Version](https://img.shields.io/pub/v/flutter_chat_ui?logo=flutter&color=orange)](https://pub.dev/packages/flutter_chat_ui) [![Pub Likes](https://img.shields.io/pub/likes/flutter_chat_ui?logo=flutter&color=orange&label=pub%20likes)](https://pub.dev/packages/flutter_chat_ui) [![Stars](https://img.shields.io/github/stars/flyerhq/flutter_chat_ui?style=flat&color=orange&logo=github)](https://github.com/flyerhq/flutter_chat_ui/stargazers) [![melos](https://img.shields.io/badge/maintained%20with-melos-ffffff.svg?color=orange)](https://github.com/invertase/melos)

Flyer Chat is an open-source chat UI package for Flutter applications, designed for performance, customization, and ease of integration.

## ✨ Features

- 🔄 **Backend-agnostic**: Connect to any backend service.
- 🎨 **Highly Customizable**: Tailor the UI with extensive theme options and builder functions.
- 🧩 **Modular**: Pick and choose the features you want. You can change any part of the UI or swap it with your own custom implementation.
- ⚡ **Performance Optimized**: Built for speed and smooth animations.
- 🌐 **Cross-Platform**: Supports iOS, Android, Web, macOS, Windows, and Linux.
- 📜 **Open Source**: Free to use under the Apache 2.0 License.

## 🚀 Installation

Add the package to your `pubspec.yaml`:

```yaml
dependencies:
  flutter_chat_core: ^ # Use the latest version
  flutter_chat_ui: ^2.0.0
```

Then, import and use the `Chat` widget.

## 📖 Basic Usage

```dart
import 'package:flutter/material.dart';
import 'package:flutter_chat_ui/flutter_chat_ui.dart';
import 'package:flutter_chat_core/flutter_chat_core.dart';

@override
Widget build(BuildContext context) {
  return Chat(
    // A simple in-memory chat controller, you can create your own controller.
    // See example project.
    chatController: InMemoryChatController(),
    // Current user id (the one that sends messages)
    currentUserId: 'user1',
    onMessageSend: (text) {
      _chatController.insert(
        TextMessage(
          // Better to use UUID or similar for the id :)
          id: '${Random().nextInt(1000) + 1}',
          authorId: 'user1',
          createdAt: DateTime.now().toUtc(),
          text: text,
        ),
      );
    },
    // Return a user object for the given id - this way chat always gets
    // latest user data.
    resolveUser: (String id) async {
      return User(id: id, firstName: 'John', lastName: 'Doe');
    },
  );
}
```

## 📚 Documentation & Examples

For detailed usage, customization options, different message types, controllers, and more complex scenarios, please refer to the **full documentation**:

➡️ **[flyer.chat/docs/flutter](https://flyer.chat/docs/flutter)** ⬅️

Explore the comprehensive [example application](https://github.com/flyerhq/flutter_chat_ui/tree/main/examples/flyer_chat) to see various features and customizations in action.

## 🤝 Contributing

Contributions are welcome! Please see the [CONTRIBUTING.md](https://github.com/flyerhq/flutter_chat_ui/blob/main/CONTRIBUTING.md) file in the main repository for guidelines.

## 📜 License

Licensed under the Apache License, Version 2.0. See the [LICENSE](https://github.com/flyerhq/flutter_chat_ui/blob/main/packages/flutter_chat_ui/LICENSE) file for details.
