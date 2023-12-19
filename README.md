# flutter-base-project

### Code Convention
- **import**
```dart
// import 순서
// 1. dart package
// 2. flutter package
// 3. external package
// 4. local package
// 5. direct import file
// 6. part
//
// 다른 종류의 import 구문이 사용될 경우 줄바꿈을 해준다.
// 같은 종류의 import 구문일 경우 바로 아래에 작성한다.
// 같은 종류의 import 구문에는 'A-Z' 순으로 정렬한다.

// 예시
import 'dart:async'; 

import 'package:flutter/material.dart';
import 'package:flutter/services.dart';

import 'package:rxdart/rxdart.dart';

import 'package:flutter_base_project/presentation/presentation.dart';

import 'test_file_util.dart';

part 'test_file.freezed.dart';
part 'test_file.g.dart';
```

- **export**
```dart
// 최상위 폴더의 index 파일은 해당 폴더의 이름을 따라간다.
// 이 외의 index 파일은 index.dart 로 지정한다.
// 'A-Z' 순으로 정렬한다.

// 예시
// lib/presentation/core/index.dart
export 'view_model/index.dart';
export 'view_state/index.dart';

// lib/presentation/presentation.dart
export 'core/index.dart';
```

- **class**
```dart
abstract class ExampleParent {
    void init();
}

class ExampleChild extends ExampleParent {
    final _exampleService = locator<ExampleService>();
    final _exampleRepository = locator<ExampleRepository>();

    ExampleChild({
        required this.message,
    });

    final String message;

    bool _hasError = false;
    String? _errorMessage;

    bool get hasError => _hasError;
    String? get errorMessage => _errorMessage;

    @override
    void init() {}

    void _removeError() {
        _hasError = false;
        _errorMessage = null;
    }

    ...
}
```