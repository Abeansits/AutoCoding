Version 2.1

- Removed automatic NSCopying implementation (see README for details)
- The +codableProperties method will no longer include properties whose ivars are not KVC compliant, even if they are readwrite. This makes it easier to mark readwrite properties as unencodable without neededing to override methods
- The +uncodableProperties method is now deprecated
- dictionaryRepresentation method will now no longer include NSNull entries for nil values (these will simply be omitted from the result instead)
- Now complies with the -Weverything warning level

Version 2.0.3

- Now complies with the -Wextra warning level

Version 2.0.2

- Fixed longstanding issue where uncodableProperties / uncodableKeys was ignored for private properties. 

Version 2.0.1

- Fixed bug where AutoCoding's NSCopying implementation was not compatible with properties using copy semantics due to lack of a copyWithZone: implementation.
- Now returns YES for respondsToSelector:@selector(copyWithZone:).

Version 2.0

- AutoCoding now implements the NSSecureCoding protocol automatically
- AutoCoding now detects property types automatically and throws an exception by default if encoded classes to not match the expected type
- Autocoding 2.0 is data-compatible with previous releases, but may require code changes when upgrading.

Version 1.3.1

- Fixed issue with CoreData where AutoCoding's copyWithZone: implementation conflicted with NSManagedObjects
- Due to changes in the automatic NSCopying implementation, calling `[super copyWithZone:]` will no longer work. If you need to do this, override the `copy` method and call `[super copy]` instead
- Added Podspec file

Version 1.3

- AutoCoding no longer attempts to encode virtual properties. Only ivar-backed properties will be encoded
- Added dictionaryRepresentation method for quickly accessing all properties of a class
- The codableKeys and uncodableKeys methods are now class methods, allowing them to be used more easily in factory methods 
- The class-level codable/uncodableKeys methods now only return the properties for the class on which they are called, not all of its superclasses as well
- It is no longer necessary to call [super codableKeys] or [super uncodableKeys] and merge arrays when overriding the codableKeys or uncodableKeys class methods on a subclass (overriding the codableKeys instance method is not recommended)

Version 1.2.1

- writeToFile:atomically: method now returns a BOOL to indicate success
- Changed category file names

Version 1.2

- Read-only properties can now be copied and coded as long as they have a KVC compliant ivar (i.e. one whose name matches the property or the property with the _ prefix)
- initWithCoder: no longer calls [self init], in compliance with Apple docs
- codableKeys method now uses caching for better performance
- Exposed previously private setWithCoder: method used by BaseModel library

Version 1.1.2

- Switched constructor to return new type-safe `instancetype` instead of id, making it easier to use dot-syntax property accessors on loaded instances.

Version 1.1.1

- Read-only properties are now excluded from codableKeys
- Added unit tests

Version 1.1

- Added automatic NSCopying implementation
- writeToFile now obeys the useAuxiliaryFile parameter

Version 1.0

- Initial release