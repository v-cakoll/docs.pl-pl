---
ms.openlocfilehash: d85fb8df7afdc5f4c3faecebcd24d11677798bc9
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365621"
---
### <a name="microsoftdotnetplatformabstractions-package-removed"></a>Usunięto pakiet Microsoft. DotNet. PlatformAbstractions

Nie zostaną wygenerowane żadne nowe wersje [pakietu NuGet Microsoft. dotnet. PlatformAbstractions](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) .

#### <a name="change-description"></a>Zmień opis

Wcześniej nowe wersje <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> biblioteki zostały utworzone wraz z nowymi wersjami programu .NET Core. W przód do biblioteki nie zostaną dodane żadne nowe funkcje i nie zostaną wydane żadne nowe wersje główne. Jednak istniejące wersje biblioteki będą nadal działać i będą obsługiwane.

<xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName>Biblioteka pokrywa się z interfejsami API, które są już ustanowione w systemie. \* przestrzenie nazw. Ponadto niektóre <xref:Microsoft.DotNet.PlatformAbstractions> interfejsy API nie zostały zaprojektowane z tym samym poziomem kontroli i długoterminową obsługą jako resztą systemu. \* Programowania. Na przykład program <xref:Microsoft.DotNet.PlatformAbstractions> używa `Platform` wyliczenia do opisywania bieżącej platformy systemu operacyjnego. Ten projekt wyliczenia został jawnie odrzucony <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> , gdy interfejs API został zaprojektowany, aby umożliwić korzystanie z nowych platform i w przyszłości.

Scenariusze włączane przez <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> bibliotekę są teraz możliwe bez niej. Istniejące wersje będą nadal działać, nawet w programie .NET 5,0 lub nowszym i będą obsługiwane wraz z poprzednimi wersjami platformy .NET Core. Jednak nowe funkcje nie zostaną dodane do biblioteki. Zamiast tego nowe funkcje zostaną dodane do innych bibliotek i interfejsów API.

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 6

#### <a name="recommended-action"></a>Zalecana akcja

- Można nadal używać starszych wersji biblioteki, jeśli spełniają one wymagania.

- Jeśli starsze wersje nie spełniają Twoich wymagań, Zastąp użycie `PlatformAbstractions` interfejsów API zalecanymi zamiennikami.

  | `PlatformAbstractions`INTERFEJSU API | Zalecane zastąpienie |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> i <xref:System.Environment.OSVersion?displayProperty=nameWithType> |

  > [!NOTE]
  > Większość przypadków użycia dla `RuntimeEnvironment.OperatingSystem` i służy `RuntimeEnvironment.OperatingSystemVersion` do wyświetlania, na przykład wyświetlania użytkownikowi, rejestrowania i telemetrii. Nie zaleca się przeprowadzania decyzji w czasie wykonywania na podstawie wersji systemu operacyjnego. <xref:System.Environment.OSVersion?displayProperty=nameWithType>teraz zwraca poprawną wersję dla systemów operacyjnych Windows i macOS. Jednak w przypadku większości dystrybucji systemu UNIX, co jest uznawane za "wersję systemu operacyjnego", nie jest tak proste. Może to być na przykład wersja jądra systemu Linux lub wersja dystrybucji. Dla większości platform systemu UNIX <xref:System.Environment.OSVersion?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> zwracają wersję zwracaną przez program `uname` . Aby uzyskać informacje o nazwie i wersji systemu Linux, zalecane podejście polega na odczytaniu pliku */etc/OS-Release* .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

#### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
