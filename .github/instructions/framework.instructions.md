---
applyTo: "**/*.cs,**/*.xaml,**/*.razor,**/*.razor.css"
---

# Framework Guidelines (C#, .NET MAUI & Blazor Hybrid)

## C# & .NET 10

- Always use **C# 14** features: extension members/properties/operators, null-conditional assignment (`?.` on left-hand side), `field`-backed properties, implicit `Span<T>` conversions, `nameof` with unbound generics, partial constructors, `params` collections, etc.
- Use file-scoped namespaces (`namespace Foo;` not `namespace Foo { }`).
- Use `required` properties for mandatory model fields instead of constructor parameters where appropriate.
- Use `record` or `record struct` for immutable data (e.g. tab state snapshots).
- Prefer pattern matching and switch expressions over if/else chains.
- `Nullable` is enabled — never suppress warnings without an explanatory comment.
- Use `ILogger<T>` for all logging — never `Console.WriteLine` in production code.
- Follow MVVM for stateful logic outside of Blazor components.
- Write XML doc comments (`///`) on all public APIs.

## .NET MAUI

- Target `net10.0-maccatalyst` and `net10.0-windows10.0.19041.0` only — never add Android, iOS, or Tizen targets.
- Use `MauiAppBuilder` and extension methods in `MauiProgram.cs` for all service registration.
- XAML source generation is enabled (`MauiXamlInflator=SourceGen`) — do not disable it.
- Platform-specific code belongs in `Platforms/MacCatalyst/` or `Platforms/Windows/` using partial classes or `#if` directives — never use runtime OS checks.
- Use `Microsoft.Maui.Controls` APIs only — no Xamarin.Forms patterns.
- The app shell is a single `MainPage.xaml` hosting a `BlazorWebView` — keep MAUI/XAML code minimal and delegate UI logic to Blazor components.

## Blazor Hybrid

- All UI lives in `Components/` — pages under `Components/Pages/`, shared layouts under `Components/Layout/`.
- Use `@inject` for dependency injection in Razor components.
- Prefer `EventCallback` over `Action` for component event parameters.
- Use CSS isolation (`.razor.css`) for component-scoped styles — avoid adding styles to global `app.css` unless truly global.
- The tabbed editor is the core UI — each open note is a tab with its own state (content, file path, dirty flag).
- Before closing a tab with unsaved changes, always prompt the user to save.
- Tabs must support saving content as a file (text or other formats) using the platform file picker.
