# restorable_nested_scroll_view

A `NestedScrollView` widget that can restore its scroll position with a `PageStorageKey`.

## Usage

```dart
import 'package:restorable_nested_scroll_view/restorable_nested_scroll_view.dart'
    as restorable;

final key = const PageStorageKey("MyKey");

restorable.NestedScrollView(
  key: key,
  headerSliverBuilder: (context, innerBoxIsScrolled) => [
    restorable.SliverOverlapAbsorber(
      handle:
          restorable.NestedScrollView.sliverOverlapAbsorberHandleFor(
        context,
      ),
      sliver: const SliverAppBar()
    ),
  ],
  body: Builder(
    builder: (context) => CustomScrollView(
      slivers: [
        restorable.SliverOverlapInjector(
          handle: restorable.NestedScrollView
              .sliverOverlapAbsorberHandleFor(
            context,
          ),
        ),
        widget.child
      ],
    ),
  ),
),
```
