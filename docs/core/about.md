---
title: Omówienie platformy .NET Core
description: Dowiedz się więcej o charakterystyce i składzie programu .NET Core i porównaj ją z innymi implementacjami platformy .NET.
ms.date: 09/17/2019
ms.openlocfilehash: f2f97fe6a5f822266582c443fd916c270cb0cb6a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345203"
---
# <a name="net-core-overview"></a>Omówienie platformy .NET Core

Program .NET Core ma następujące właściwości:

- **Międzyplatformowe:** Działa w [systemach operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS i Linux .
- **Spójne w różnych architekturach:** Uruchamia kod z tym samym zachowaniem na wielu architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:**  Zawiera łatwe w użyciu narzędzia wiersza polecenia, które mogą być używane do lokalnego rozwoju i w scenariuszach ciągłej integracji.
- **Elastyczne wdrażanie:** Może być dołączony do aplikacji lub zainstalowany obok siebie (instalacje dla całego użytkownika lub całego systemu). Może być używany z [kontenerami platformy Docker](docker/introduction.md).
- **Kompatybilny:** .NET Core jest zgodny z implementacjami .NET Framework, Xamarin i Mono za pośrednictwem [platformy .NET Standard.](../standard/net-standard.md)
- **Open source:** Platforma .NET Core jest open source, przy użyciu licencji MIT i Apache 2. .NET Core to projekt [.NET Foundation.](https://dotnetfoundation.org/)
- **Obsługiwane przez firmę Microsoft:** .NET Core jest [obsługiwane przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Języki

Języki C#, Visual Basic i F# mogą być używane do pisania aplikacji i bibliotek dla platformy .NET Core. Te języki mogą być używane w ulubionym edytorze tekstu lub zintegrowanym środowisku programistycznym (IDE), w tym:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Kod programu Visual Studio](https://code.visualstudio.com/download)
- Wysublimowy tekst
- Vim

Integracja edytora jest częściowo świadczona przez współautorów projektów [OmniSharp](https://www.omnisharp.net/) i [Ionide.](http://ionide.io)

## <a name="apis"></a>Interfejsy API

Wiele interfejsów API są zawarte, które spełniają wspólne potrzeby, takie jak:

- Typy pierwotne, <xref:System.Boolean?displayProperty=nameWithType> takie <xref:System.Int32?displayProperty=nameWithType>jak i .
- Kolekcje, takie <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>jak i .
- Typy narzędzi, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>takie <xref:System.IO.FileStream?displayProperty=nameWithType>jak , i .
- Typy danych, <xref:System.Data.DataSet?displayProperty=nameWithType>takie jak , i [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Typy o wysokiej <xref:System.Numerics.Vector?displayProperty=nameWithType> wydajności, takie jak [i Potoki](../standard/io/pipelines.md).

Program .NET Core zapewnia zgodność z interfejsami API platformy .NET Framework i mono, implementując specyfikację [standardu .NET.](../standard/net-standard.md)

## <a name="frameworks"></a>Struktury

Wiele struktur zostało zbudowanych na podstawie programu .NET Core, w tym:

- [ASP.NET Core](/aspnet/core/)
- [Platforma uniwersalna systemu Windows (UWP)](/windows/uwp/)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Kompozycja

Program .NET Core składa się z następujących części:

- [Środowisko uruchomieniowe .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), który zapewnia system typów, ładowanie zestawu, moduł zbierający elementy bezużyteczne, natywne interop i inne podstawowe usługi. [Biblioteki .NET Core framework](https://github.com/dotnet/runtime/tree/master/src/libraries) zapewniają podstawowe typy danych, typy kompozycji aplikacji i podstawowe narzędzia.
- [Środowisko wykonawcze ASP.NET Core](https://github.com/dotnet/aspnetcore), które zapewnia platformę do tworzenia nowoczesnych, opartych na chmurze aplikacji połączonych z Internetem, takich jak aplikacje internetowe, aplikacje IoT i zaplecze mobilne.
- [Kompilatora zestawu .NET Core SDK](https://github.com/dotnet/sdk) i języka[(Roslyn](https://github.com/dotnet/roslyn) i [F#),](https://github.com/microsoft/visualfsharp)które umożliwiają środowisko deweloperskie .NET Core.
- [Polecenie dotnet](./tools/dotnet.md), które służy do uruchamiania aplikacji .NET Core i poleceń interfejsu wiersza polecenia. Wybiera i obsługuje środowisko uruchomieniowe, udostępnia zasady ładowania zestawu i uruchamia aplikacje i narzędzia.

Składniki te są rozmieszczone w następujący sposób:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) — zawiera biblioteki środowiska uruchomieniowego i framework.NET Core.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) — obejmuje środowiska wykonawcze ASP.NET Core i .NET Core oraz biblioteki ramowe.
- [.NET Core SDK](https://dotnet.microsoft.com/download) — zawiera środowisko interfejsu wiersza polecenia .NET Core, ASP.NET core oraz środowisko uruchomieniowe i strukturę .NET Core.

### <a name="open-source"></a>Kod open source

[.NET Core](https://github.com/dotnet/core) jest open-source[(licencja MIT)](https://github.com/dotnet/core/blob/master/LICENSE.TXT)i został dodany do [.NET Foundation](https://dotnetfoundation.org) przez Microsoft w 2014. Jest to obecnie jeden z najbardziej aktywnych projektów .NET Foundation. Może być używany przez osoby fizyczne i firmy, w tym do celów osobistych, akademickich lub komercyjnych. Wiele firm używa platformy .NET Core jako części aplikacji, narzędzi, nowych platform i usług hostingowych. Niektóre z tych firm wnoszą znaczący wkład do platformy .NET Core na GitHub i dostarczają wskazówek dotyczących kierunku produktu w ramach [technicznej grupy sterującej .NET Foundation.](https://dotnetfoundation.org/blog/tsg-welcome)

### <a name="designed-for-adaptability"></a>Zaprojektowane z myślą o możliwości adaptacji

Program .NET Core został zbudowany jako podobny, ale unikatowy produkt w porównaniu z innymi produktami platformy .NET. Został zaprojektowany, aby umożliwić szerokie dostosowanie do nowych platform i obciążeń i ma kilka portów systemu operacyjnego i procesora (i może być przeniesiony do wielu innych).

Produkt jest podzielony na kilka części, dzięki czemu poszczególne części mogą być dostosowane do nowych platform w różnym czasie. Biblioteki podstawowe środowiska wykonawczego i specyficzne dla platformy muszą być przenoszone jako jednostka. Biblioteki niezależne od platformy powinny działać tak, jak jest na wszystkich platformach, przez budowę. Istnieje błąd projektu w kierunku zmniejszenia implementacji specyficznych dla platformy, aby zwiększyć wydajność dewelopera, preferując kod C# neutralny dla platformy, gdy algorytm lub interfejs API może być zaimplementowany w całości lub w części w ten sposób.

Ludzie często pytają, jak .NET Core jest implementowany w celu obsługi wielu systemów operacyjnych. Zazwyczaj pytają, czy istnieją oddzielne implementacje lub jeśli używana jest [kompilacja warunkowa.](https://en.wikipedia.org/wiki/Conditional_compilation) To jedno i drugie, z silnym nastawieniem do kompilacji warunkowej.

Na poniższym wykresie widać, że zdecydowana większość [bibliotek .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) jest kompilowana z kodu neutralnego dla platformy, który jest udostępniany na wszystkich platformach. Kod neutralny dla platformy może być zaimplementowany jako pojedynczy przenośny zestaw, który jest używany na wszystkich platformach.

![CoreFX: Linie kodu na platformę](../images/corefx-platforms-loc.png)

Implementacje systemu Windows i Unix mają podobny rozmiar. Implementacja systemu Windows zawiera niektóre funkcje systemu Windows, takie jak [Microsoft.Win32.Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry), ale nie implementuje jeszcze wielu pojęć tylko uniksowych. Większość implementacji systemu Linux i macOS jest współużytkowana przez implementację Uniksa. Implementacje specyficzne dla systemu Linux i macOS mają podobny rozmiar.

W ramach programu .NET Core istnieje połączenie bibliotek specyficznych dla platformy i platformy. Wzór można zobaczyć w kilku przykładach:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) jest specyficzny dla platformy. Opiera się na podsystemach systemu operacyjnego, takich jak menedżer pamięci i harmonogram wątków.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) i [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) są specyficzne dla platformy, biorąc pod uwagę, że interfejsy API pamięci masowej i kryptografii są różne w każdym systemie operacyjnym.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) i [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) są neutralne dla platformy, biorąc pod uwagę, że tworzą i działają nad strukturami danych.

## <a name="comparisons-to-other-net-implementations"></a>Porównania z innymi implementacjami platformy .NET

Aby zrozumieć rozmiar i kształt programu .NET Core, w poniższych sekcjach porównano go z istniejącymi implementacjami platformy .NET.

### <a name="net-core-vs-net-framework"></a>.NET Core vs. .NET Framework

.NET został po raz pierwszy ogłoszony przez Microsoft w 2000 roku i ewoluował stamtąd. Program .NET Framework jest podstawową implementacją platformy .NET opracowaną przez firmę Microsoft w ciągu prawie dwóch dekad.

Główne różnice między programem .NET Core a platformą .NET Framework to:

- **Modele aplikacji** -- .NET Core nie obsługuje wszystkich modeli aplikacji .NET Framework. W szczególności nie obsługuje ASP.NET formularzy sieci Web i ASP.NET MVC, ale obsługuje ASP.NET Core MVC. Począwszy od platformy .NET Core 3.0, program .NET Core obsługuje również w systemie Windows tylko w systemie Windows w systemie Windows.
- **Interfejsy API** -- .NET Core zawiera duży podzbiór biblioteki klas podstawowych programu .NET Framework z innym faktoringiem (nazwy zestawów są różne; elementy członkowskie widoczne dla typów różnią się w kluczowych przypadkach). W niektórych przypadkach te różnice wymagają zmiany źródła portu na .NET Core. Aby uzyskać więcej informacji, zobacz [Analizator przenośności .NET](../standard/analyzers/portability-analyzer.md). Program .NET Core implementuje specyfikację standardowego interfejsu API [platformy .NET.](../standard/net-standard.md)
- **Podsystemy** -- .NET Core implementuje podzbiór podsystemów w programie .NET Framework, w celu prostszej implementacji i modelu programowania. Na przykład kod access security (CAS) nie jest obsługiwany, podczas gdy odbicie jest obsługiwane.
- **Platformy** -- .NET Framework obsługuje systemy Windows i Windows Server, podczas gdy .NET Core obsługuje również systemy macOS i Linux.
- **Open source** -- .NET Core jest open source, podczas gdy [podzbiór tylko do odczytu .NET Framework](https://github.com/microsoft/referencesource) jest open source.

Program .NET Core jest unikatowy i ma znaczące różnice w programie .NET Framework i innych implementacjach platformy .NET, ale udostępnianie kodu między tymi implementacjami jest proste przy użyciu technik udostępniania źródłowego lub binarnego.

Ponieważ program .NET Core obsługuje instalację side-by-side, a jej środowisko wykonawcze jest całkowicie niezależne od platformy .NET Framework, można go zainstalować na komputerach z zainstalowanym programem .NET Framework bez żadnych problemów.

### <a name="net-core-vs-mono"></a>.NET Core vs. Mono

[Mono](https://www.mono-project.com/) jest oryginalną implementacją platformy .NET. Zaczęło się jako [alternatywa open-source](https://github.com/mono/mono) dla platformy .NET Framework i przejście do kierowania na urządzenia mobilne, ponieważ urządzenia z systemami iOS i Android stały się popularne. Można go traktować jako klon społeczności .NET Framework. Aby zapewnić zgodną implementację, zespół projektu Mono oparł się na otwartych [standardach .NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (zwłaszcza ECMA 335) opublikowanych przez firmę Microsoft.

Główne różnice między .NET Core i Mono są:

- **Modele aplikacji** — mono obsługuje podzbiór modeli aplikacji platformy .NET Framework (na przykład formularze systemu Windows) i niektóre dodatkowe dla rozwoju urządzeń przenośnych (na przykład [Xamarin.iOS)](https://www.xamarin.com/platform)za pośrednictwem produktu platformy Xamarin. .NET Core nie obsługuje platformy Xamarin.
- **Interfejsy API** — mono obsługuje [duży podzbiór](http://docs.go-mono.com/?link=root%3a%2fclasslib) interfejsów API programu .NET Framework, przy użyciu tych samych nazw zestawów i faktoringu.
- **Platformy** - Mono obsługuje wiele platform i procesorów.
- **Open Source** — mono i .NET Core używają licencji MIT i są projektami .NET Foundation.
- **Fokus** - Głównym celem Mono w ostatnich latach są platformy mobilne, podczas gdy .NET Core koncentruje się na obciążeniach w chmurze i komputerach stacjonarnych.

## <a name="support"></a>Pomoc techniczna

Program .NET Core jest [obsługiwany przez firmę Microsoft](https://dotnet.microsoft.com/platform/support/policy) w systemach Windows, macOS i Linux. Jest regularnie aktualizowany pod kątem bezpieczeństwa i jakości (drugi wtorek każdego miesiąca).

Dystrybucje binarne .NET Core firmy Microsoft są tworzone i testowane na serwerach obsługiwanych przez firmę Microsoft na platformie Azure i stosują się do praktyk inżynieryjnych i zabezpieczeń firmy Microsoft.

[Red Hat obsługuje .NET Core](http://redhatloves.net/) na Red Hat Enterprise Linux (RHEL). Red Hat buduje .NET Core ze źródła i udostępnia go w [red hat software collections](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat i Microsoft współpracują, aby zapewnić, że program .NET Core działa dobrze na RHEL.

[Tizen obsługuje platformy .NET Core](https://developer.tizen.org/development/training/.net-application) na platformach Tizen.
