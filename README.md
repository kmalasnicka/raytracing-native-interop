# Ray Tracing — Native Code Interoperability

A C# project developed as part of a Programming 3 course, demonstrating interoperability between a native C++ ray tracing engine and a managed C# application.

The C++ core from *Ray Tracing in One Weekend* is compiled as a native shared library and called from C# via P/Invoke. The application renders the classic book cover scene in real time, displaying progressive updates in an Avalonia-based window.

## Implementation

- **Native layer (C++)** — C-compatible export functions with opaque handles for scene and material objects, a `RenderScene` function with a progress callback, and `SavePng` for image output via `stb_image_write`
- **Low-level bindings (C#)** — P/Invoke declarations using `[LibraryImport]`, `SafeHandle`-based wrappers for automatic resource cleanup
- **High-level API (C#)** — idiomatic object-oriented wrapper implementing `IDisposable`, hiding all raw pointers from the consumer
- **Demo application** — procedurally generated book cover scene with live rendering progress displayed in an Avalonia window; final image saved as `output.png`