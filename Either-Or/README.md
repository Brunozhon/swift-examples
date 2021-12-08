# Either-Or

In Swift, you can't include two types in one. What do you do? With the simple Either-Or enum, you can include two types in one in some easy steps!!

**Step One:** Declare the enum like this:
```swift
enum EitherOr<EitherType, OrType> {
  
}
```

**Step Two:** Add two cases to the enum: `either` and `or` with their associated types. (This should be easy. You know you shouldn't write `either(OrType)` or `or(EitherType)`)
```swift
enum EitherOr<EitherType, OrType> {
  case either(EitherType)
  case or(OrType)
}
```

**Step Three:** Declare an extension for `EitherOr` that conforms it to both `Hashable` and `Equatable` where `EitherType` and `OrType` conform to `Hashable`. You don't know what I mean? Here's the code:
```swift
extension EitherOr: Hashable, Equatable where EitherType: Hashable, OrType: Hashable {}
```

> **Note:** You must conform it to both `Hashable` and `Equatable` or you'll get:
>
> > **Conditional conformance of type `EitherOr<EitherType, OrType>` does not imply conformance to inherited protocol `Equatable`.**
> >
> > Did you mean to explictly state the conformance like `extension EitherOr: Hashable, Equatable where EitherType: Hashable, OrType: Hashable {}`?

But anyways, you know what the error means, do you? The only changes I made are shown below.

extension EitherOr: **Hashable,** Equatable where ~...~ **EitherType: Hashable, OrType: Hashable {}**

That's how you do it!
