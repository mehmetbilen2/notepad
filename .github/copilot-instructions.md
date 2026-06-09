# Copilot Instructions for NoteThings

## Project Overview

NoteThings is a cross-platform note-taking app built with .NET MAUI Blazor Hybrid.
It targets **macOS (Mac Catalyst)** and **Windows** only — no Android, iOS, or Tizen.

## Tech Stack & Versions

- **SDK**: .NET 10 (net10.0-maccatalyst, net10.0-windows10.0.19041.0)
- **Language**: C# 14 — always use the latest language features
- **UI framework**: .NET MAUI Blazor Hybrid (`BlazorWebView` inside a MAUI shell)
- **Dependency injection**: `MauiProgram.cs` using `MauiAppBuilder`

## Coding Guidelines

### C# & .NET

- Always use **C# 14** features where applicable: extension members/properties/operators, null-conditional assignment, `field`-backed properties, implicit `Span<T>` conversions, partial constructors, `params` collections, etc.
- Prefer `file`-scoped namespaces.
- Use `required` properties instead of constructor injection for simple models.
- Use `record` or `record struct` for immutable data models.
- Prefer pattern matching and switch expressions over if/else chains.
- Always enable and respect `Nullable` — never suppress nullability warnings without a comment.
- Use `ILogger<T>` for logging; never use `Console.WriteLine` in production code.

### .NET MAUI

- Use the latest MAUI APIs — prefer `MauiAppBuilder` extension methods over legacy patterns.
- XAML source generation is enabled (`MauiXamlInflator=SourceGen`) — do not disable it.
- Platform-specific code goes in `Platforms/MacCatalyst/` or `Platforms/Windows/` using `#if` preprocessor or partial classes, not runtime checks.
- Use `Microsoft.Maui.Controls` APIs; do not introduce Xamarin.Forms patterns.

### Blazor Hybrid

- Components live in `Components/` — pages under `Components/Pages/`, shared layouts under `Components/Layout/`.
- Use `@inject` for DI in Razor components.
- Prefer `EventCallback` over `Action` for component event parameters.
- CSS isolation (`.razor.css`) is preferred over global styles for component-scoped styles.

### General

- Follow **MVVM** for any stateful logic that lives outside of a Blazor component.
- Do not add mobile (Android/iOS/Tizen) target frameworks or platform folders.
- Keep NuGet packages up to date with .NET 10 compatible versions.
- Write XML doc comments (`///`) on all public APIs.
