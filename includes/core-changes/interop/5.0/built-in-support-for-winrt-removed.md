---
ms.openlocfilehash: d21b2e092d460fdfc367d0f490228ed44ad5c6cc
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365658"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a>Wbudowana obsługa środowiska WinRT jest usuwana z platformy .NET

Wbudowana obsługa użycia interfejsów API [środowiska wykonawczego systemu Windows](/uwp/winrt-cref/winrt-type-system) w programie .NET jest usuwana.

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 6

#### <a name="change-description"></a>Zmień opis

Wcześniej CoreCLR może zużywać [pliki metadanych systemu Windows (WinMD)](/uwp/winrt-cref/winmd-files) do aktywnych i korzystać z typów WinRT. Począwszy od platformy .NET 5,0, CoreCLR nie może już bezpośrednio korzystać z plików WinMD.

Jeśli próbujesz odwołać się do nieobsługiwanego zestawu, uzyskasz <xref:System.IO.FileNotFoundException> . W przypadku aktywowania klasy WinRT uzyskasz <xref:System.PlatformNotSupportedException> .

Ta nieprzerwana zmiana została wprowadzona z następujących powodów:

- Dlatego WinRT można opracowywać i ulepszyć niezależnie od środowiska uruchomieniowego .NET.
- Dla symetrii z systemami międzyoperacyjnymi udostępnianymi dla innych systemów operacyjnych, takich jak iOS i Android.
- W celu skorzystania z innych funkcji platformy .NET, takich jak funkcje języka C#, konsolidacja w języku pośrednim (IL) i kompilacja przed czasem (AOT).
- Aby uprościć bazę kodu środowiska uruchomieniowego platformy .NET.

#### <a name="recommended-action"></a>Zalecana akcja

- Usuń odwołania do [pakietu Microsoft. Windows. Sdk.](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts) Contracts i zastąp je odwołaniami do [pakietu Microsoft.Windows.Sdk.NET](https://www.nuget.org/packages/microsoft.windows.sdk.net).

- Za pomocą łańcucha narzędzi [/WinRT języka C#](/windows/uwp/csharp-winrt/) można generować lub dostosowywać interfejsy API i typy środowiska WinRT w programie .NET 5,0 i nowszych wersjach.

#### <a name="category"></a>Kategoria

Interop

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
