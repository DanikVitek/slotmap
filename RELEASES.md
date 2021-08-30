Version 0.3.2
=============

 - Made Key trait unsafe, as it was erroneously safe to implement.


Version 0.3.1
=============

 - Backport of fixes from 1.0.4 and 1.0.5.


Version 0.3.0
=============

 - Massive rework, with a focus on secondary maps and custom keys to prevent
   cross-slotmap key usage.

 - Removed `DenseSlotMap` in favour of `HopSlotMap` as the latter performs
   better when secondary maps are in use.

 - Added `SecondaryMap` and `SparseSecondaryMap`, which allows you to associate
   extra data with keys given by a slot map. 

 - Added `DefaultKey`, custom key types, and support for them on all slot maps
   and secondary maps. You must now always specify the key type you're using
   with a slot map, so `SlotMap<i32>` would be `SlotMap<DefaultKey, i32>`. It is
   recommended to make a custom key type with `new_key_type!` for any slot map
   you create, as this entirely prevents using the wrong key on the wrong slot
   map.

 - `KeyData` now has `as_ffi` and `from_ffi` functions that convert the data
   that makes up a key to/from an `u64`. This allows you to use slot map keys
   as opaque handles in FFI code.


Version 0.2.1
=============

 - Fixed a potential uninitialized memory vulnerability. No uninitialized memory
   was read or used directly, but Rust's assumptions could lead to it. Yanked
   all previous versions as they were all vulnerable.

 - Made a `Key` member non-zero so that `Option<Key>` is optimized.


Version 0.2.0
=============
Start of version history.
