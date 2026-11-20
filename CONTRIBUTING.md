# Contributing & Build Guide — NailoongAdventure 🐉

## 1. Zero-Asset Procedural Architecture

**NailoongAdventure** is built on **Unity 6.3 LTS** with a strict **zero external asset** invariant:
- Every mesh, material, rig (`SkinnedMeshRenderer`), animation curve, sound effect, and UI canvas is synthesized procedurally in C# under `Assets/NailoongAdventure/`.
- When adding new procedural meshes to `SkinnedMeshRenderer`, **always** set `smr.localBounds = mesh.bounds` and `smr.updateWhenOffscreen = true` so WebGL/IL2CPP frustum culling never clips the mesh.
- When adding serializable `[Serializable]` save-state structs used by `JsonUtility`, ensure they remain under the `Nailoong` namespace protected by `Assets/NailoongAdventure/link.xml` (`ManagedStrippingLevel.High`).

## 2. Building Locally

- **Windows Standalone Build**: Run `build.bat`
- **WebGL Build + Static Landing Page Bundle**: Run `build_webgl.bat` followed by `node build-site.js`
- **Cloudflare Pages Deployment**: Configured via `wrangler.toml` and `_headers` (do not re-enable `Cross-Origin-Embedder-Policy: require-corp` unless single-threaded WebGL is switched to `SharedArrayBuffer` pthreads with explicit CORP headers on `*.unityweb`).
