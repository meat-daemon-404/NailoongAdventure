# Changelog

All notable changes to **NailoongAdventure (奶龙冒险)** (`meat-daemon-404/NailoongAdventure`) are documented in this file.

## [1.1.0] - 2026-08-30

### Fixed
- **WebGL `SkinnedMeshRenderer` Frustum Culling (`DragonFactory.Build`, `GameBuilder.PersistMeshes`)**: Explicitly assigned `smr.localBounds = mesh.bounds` and enabled `updateWhenOffscreen = true` to prevent procedural character meshes from disappearing under IL2CPP/WebGL builds when `m_AABB` defaulted to zero.
- **Cloudflare Pages WebAssembly Loading (`_headers`)**: Removed `Cross-Origin-Embedder-Policy: require-corp` / `COOP` headers that blocked `.unityweb` `.wasm` and `.data` fetches on Cloudflare Pages when upstream assets lacked explicit CORP headers.

### Improved
- **High Managed Stripping + Assembly Preservation (`GameBuilder.BuildWebGL`, `Assets/NailoongAdventure/link.xml`)**: Enabled `ManagedStrippingLevel.High` while preserving `Assembly-CSharp` (`Nailoong` namespace) for `JsonUtility` `SaveData` serialization, shrinking `.data.unityweb` (`8.4 MB -> 8.2 MB`) and `.wasm.unityweb` (`7.3 MB -> 7.1 MB`).
- **CDN Caching & Progressive Loading UX (`_headers`, `build-site.js`)**: Extended `/game/Build/*.unityweb` `Cache-Control` `max-age` from `300s` to `86400s` and injected real-time MB download progress indicators for mobile browsers.

## [1.0.0] - 2026-08-28

### Added
- **100% Procedural Unity 6.3 LTS 3D Adventure Demo**: Zero external 3D/audio assets — character meshes (`DragonFactory`), combat hitboxes, quest state machines, procedural terrain/levels, and synthesized audio generated entirely via C# code.
