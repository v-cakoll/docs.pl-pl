---
title: Informacje o platformie .NET Core
description: Dowiedz się więcej o .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147363"
---
# <a name="about-net-core"></a>Informacje o platformie .NET Core

.NET Core ma następujące cechy:

- **Międzyplatformowe:** Działa w [systemach operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, macOS i Linux .
- **Spójne w różnych architekturach:** Uruchamia kod z tym samym zachowaniem na wielu architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:**  Zawiera łatwe w użyciu narzędzia wiersza polecenia, które mogą być używane do tworzenia lokalnych i scenariuszy ciągłej integracji.
- **Elastyczne wdrażanie:** Może być zawarty w aplikacji lub zainstalowany obok siebie (instalacje obejmujące cały użytkownik lub system). Może być używany z [kontenerami platformy Docker](docker/introduction.md).
- **Zgodny:** .NET Core jest zgodny z .NET Framework, Xamarin i Mono, za pośrednictwem [.NET Standard](../standard/net-standard.md).
- **Open source:** Platforma .NET Core jest open source, korzystająca z licencji MIT i Apache 2. .NET Core jest projektem [.NET Foundation.](https://dotnetfoundation.org/)
- **Obsługiwane przez firmę Microsoft:** .NET Core jest obsługiwana przez firmę Microsoft, zgodnie z [pomocą techniczną .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Języki

Języki C#, Visual Basic i F# mogą służyć do pisania aplikacji i bibliotek dla programu .NET Core. Języków tych można używać w ulubionym edytorze tekstu lub zintegrowanym środowisku programistycznym (IDE), w tym:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Kod programu Visual Studio](https://code.visualstudio.com/download)
- Wzniosły tekst
- Vim

Ta integracja jest częściowo świadczona przez współautorów projektów [OmniSharp](https://www.omnisharp.net/) i [Jonide.](http://ionide.io)

## <a name="apis"></a>Interfejsy API

Program .NET Core udostępnia interfejsy API dla wielu scenariuszy, z których kilka należy wykonać:

- Typy pierwotne, takie <xref:System.Boolean?displayProperty=nameWithType> jak <xref:System.Int32?displayProperty=nameWithType>i .
- Kolekcje, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> takie <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>jak i .
- Typy narzędzi, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>takie <xref:System.IO.FileStream?displayProperty=nameWithType>jak , i .
- Typy danych, <xref:System.Data.DataSet?displayProperty=nameWithType>takie jak , i [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Typy o wysokiej wydajności, takie jak <xref:System.Numerics.Vector?displayProperty=nameWithType> i [potoki](../standard/io/pipelines.md).

.NET Core zapewnia zgodność z interfejsami API .NET Framework i Mono, implementując specyfikację [standardu .NET.](../standard/net-standard.md)

## <a name="frameworks"></a>Struktury

Wiele struktur zostały zbudowane na wierzchu .NET Core:

- [ASP.NET Core](/aspnet/core/)
- [Uniwersalna platforma Windows 10 dla systemu Windows (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Kompozycja

Program .NET Core składa się z następujących części:

- [Program .NET Core ,](https://github.com/dotnet/runtime/tree/master/src/coreclr)który zapewnia system typów, ładowanie zestawu, moduł zbierający elementy bezużyteczne, natywne współgranie i inne podstawowe usługi. [Biblioteki platformy .NET Core udostępniają](https://github.com/dotnet/runtime/tree/master/src/libraries) podstawowe typy danych, typy kompozycji aplikacji i podstawowe narzędzia.
- [ASP.NET Core runtime](https://github.com/dotnet/aspnetcore), który zapewnia strukturę do tworzenia nowoczesnych aplikacji internetowych opartych na chmurze, takich jak aplikacje internetowe, aplikacje IoT i zaplecza mobilne.
- [Sdk .NET Core](https://github.com/dotnet/sdk) i kompilatory języka[(Roslyn](https://github.com/dotnet/roslyn) i [F#](https://github.com/microsoft/visualfsharp)), które umożliwiają środowisko dewelopera .NET Core.
- [Polecenie dotnet](./tools/dotnet.md), które służy do uruchamiania aplikacji .NET Core i poleceń cli. Wybiera czas wykonywania i obsługuje czas wykonywania, zapewnia zasady ładowania zestawu i uruchamia aplikacje i narzędzia.

Składniki te są rozmieszczone w następujący sposób:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) - zawiera biblioteki uruchomieniowe i framework .NET Core.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) — zawiera biblioteki i biblioteki podstawowe i frameworkowe ASP.NET Core i .NET Core.
- [.NET Core SDK](https://dotnet.microsoft.com/download) — zawiera cli .NET Core, ASP.NET core runtime oraz program .NET Core i framework.

### <a name="open-source"></a>Kod open source

[.NET Core](https://github.com/dotnet/core) jest[licencją open source (licencja MIT)](https://github.com/dotnet/core/blob/master/LICENSE.TXT)i został dodłony do [.NET Foundation](https://dotnetfoundation.org) przez firmę Microsoft w 2014 roku. Jest to obecnie jeden z najbardziej aktywnych projektów .NET Foundation. Może być używany przez osoby fizyczne i firmy, w tym do celów osobistych, akademickich lub komercyjnych. Wiele firm korzysta z platformy .NET Core jako części aplikacji, narzędzi, nowych platform i usług hostingowych. Niektóre z tych firm wnoszą znaczący wkład w program .NET Core w usteercie GitHub i udzielają wskazówek dotyczących kierunku produktu w ramach [grupy sterującej technicznej .NET Foundation](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Zaprojektowane z myślą o zdolnościach adaptacyjnych

Program .NET Core został zbudowany jako podobny, ale unikalny produkt w porównaniu z innymi produktami .NET. Został zaprojektowany, aby umożliwić szerokie dostosowanie do nowych platform i obciążeń i ma kilka portów os i cpu dostępne (i może być przeniesiony do wielu innych).

Produkt jest podzielony na kilka części, co pozwala na dostosowanie różnych części do nowych platform w różnym czasie. Biblioteki podstawowe dotyczące czasu wykonywania i platformy muszą być przeniesione jako jednostka. Biblioteki niezależne od platformy powinny działać tak, jak na wszystkich platformach, przez konstrukcję. Istnieje stronniczość projektu w kierunku zmniejszenia implementacji specyficznych dla platformy w celu zwiększenia wydajności dewelopera, preferując kod C# neutralny dla platformy, gdy algorytm lub interfejs API można zaimplementować w całości lub w części w ten sposób.

Ludzie często pytają, jak program .NET Core jest implementowany w celu obsługi wielu systemów operacyjnych. Zazwyczaj pytają, czy istnieją oddzielne implementacje lub jeśli używana jest [kompilacja warunkowa.](https://en.wikipedia.org/wiki/Conditional_compilation) To jedno i drugie, z silną stronniczością w kierunku kompilacji warunkowej.

Na poniższym wykresie widać, że zdecydowana większość bibliotek .NET Core jest kodem neutralnym dla [platformy,](https://github.com/dotnet/runtime/tree/master/src/libraries) który jest współużytkowany na wszystkich platformach. Kod neutralny dla platformy można zaimplementować jako pojedynczy przenośny zestaw, który jest używany na wszystkich platformach.

![CoreFX: Linie kodu na platformę](../images/corefx-platforms-loc.png)

Implementacje systemu Windows i Unix mają podobny rozmiar. System Windows ma większą implementację, ponieważ biblioteki .NET Core implementują niektóre funkcje tylko systemu Windows, takie jak [Microsoft.Win32.Registry,](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) ale nie implementują jeszcze wielu koncepcji tylko dla systemu Unix. Zobaczysz również, że większość implementacji systemu Linux i macOS jest współużytkowana przez implementację systemu Unix, podczas gdy implementacje specyficzne dla systemu Linux i macOS mają mniej więcej podobny rozmiar.

Istnieje połączenie bibliotek specyficznych dla platformy i biblioteki neutralne dla platformy w .NET Core. Wzór można zobaczyć w kilku przykładach:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) jest specyficzny dla platformy. Opiera się na podsystemach os, takich jak menedżer pamięci i harmonogram wątków.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) i [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) są specyficzne dla platformy, biorąc pod uwagę, że interfejsy API magazynu i kryptografii są różne w każdym systemie operacyjnym.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) i [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) są neutralne pod względem platformy, biorąc pod uwagę, że tworzą i działają nad strukturami danych.

## <a name="comparisons-to-other-net-implementations"></a>Porównania z innymi implementacjami .NET

Prawdopodobnie łatwiej jest zrozumieć rozmiar i kształt programu .NET Core, porównując go z istniejącymi implementacjami .NET.

### <a name="comparison-with-net-framework"></a>Porównanie z platformą .NET Framework

.NET został po raz pierwszy ogłoszony przez Microsoft w 2000 roku, a następnie ewoluował stamtąd. .NET Framework jest podstawową implementacją .NET wyprodukowaną przez firmę Microsoft w tym okresie prawie dwóch dekad.

Główne różnice między .NET Core i .NET Framework:

- **Modele aplikacji** -- .NET Core nie obsługuje wszystkich modeli aplikacji .NET Framework. W szczególności nie obsługuje ASP.NET formularzy sieci Web i ASP.NET MVC, ale obsługuje ASP.NET Core MVC. Począwszy od .NET Core 3.0, .NET Core obsługuje również formularze WPF i Windows w systemie Windows.
- **Interfejsy API** -- .NET Core zawiera duży podzbiór biblioteki klas podstawowych .NET Framework, z inną faktoringiem (nazwy zestawów są różne; elementy członkowskie udostępniane na typy różnią się w kluczowych przypadkach). W niektórych przypadkach te różnice wymagają zmian w źródle portu do .NET Core. Aby uzyskać więcej informacji, zobacz [Analizator przenośności .NET](../standard/analyzers/portability-analyzer.md). Program .NET Core implementuje specyfikację interfejsu API [standardu .NET.](../standard/net-standard.md)
- **Podsystemy** -- .NET Core implementuje podzbiór podsystemów w programie .NET Framework w celu prostszego modelu implementacji i programowania. Na przykład zabezpieczenia dostępu do kodu (CAS) nie jest obsługiwana, podczas gdy odbicie jest obsługiwane.
- **Platformy** — program .NET Framework obsługuje systemy Windows i Windows Server, podczas gdy program .NET Core obsługuje również systemy macOS i Linux.
- **Open Source** -- .NET Core jest open source, podczas gdy [podzbiór tylko do odczytu .NET Framework](https://github.com/microsoft/referencesource) jest open source.

Podczas gdy .NET Core jest unikatowy i ma znaczące różnice w do .NET Framework i innych implementacji .NET, jest proste do udostępniania kodu między tymi implementacjami, przy użyciu technik udostępniania źródłowego lub binarnego.

Ponieważ program .NET Core obsługuje instalację obok siebie, a jej działanie jest całkowicie niezależne od platformy .NET Framework, można ją zainstalować na komputerach z zainstalowanym .NET Framework bez żadnych problemów.

### <a name="comparison-with-mono"></a>Porównanie z Mono

[Mono](https://www.mono-project.com/) to oryginalna implementacja platformy .NET. Zaczęło się jako [alternatywa open source](https://github.com/mono/mono) do .NET Framework i przesiadł się do kierowania urządzeń przenośnych, jak iOS i Android urządzenia stały się popularne. Można go traktować jako klon społeczności .NET Framework. Zespół projektu Mono oparł się na otwartych [standardach .NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (zwłaszcza ECMA 335) opublikowanych przez firmę Microsoft w celu zapewnienia zgodnej implementacji.

Główne różnice między .NET Core i Mono:

- **Modele aplikacji** — mono obsługuje podzbiór modeli aplikacji .NET Framework (na przykład formularzy systemu Windows) i niektóre dodatkowe dla rozwoju mobilnego (na przykład [Xamarin.iOS)](https://www.xamarin.com/platform)za pośrednictwem produktu Xamarin. Program .NET Core nie obsługuje programu Xamarin.
- **Interfejsy API** — mono obsługuje [duży podzbiór](http://docs.go-mono.com/?link=root%3a%2fclasslib) interfejsów API platformy .NET Framework przy użyciu tych samych nazw zestawów i faktoringu.
- **Platformy** — mono obsługuje wiele platform i procesorów.
- **Open Source** - Mono i .NET Core używają licencji MIT i są projektami .NET Foundation.
- **Focus** - Głównym celem Mono w ostatnich latach są platformy mobilne, podczas gdy .NET Core koncentruje się na obciążeniach w chmurze i komputerach stacjonarnych.

## <a name="the-future"></a>Przyszłość

Ogłoszono, że .NET 5 będzie kolejną wersją .NET Core i reprezentuje unifikację platformy. Projekt ma na celu poprawę .NET na kilka kluczowych sposobów:

- Tworzenie jednego środowiska uruchomieniowego .NET i struktury, które mogą być używane wszędzie i który ma jednolite zachowania środowiska uruchomieniowego i środowiska deweloperów.
- Rozszerz możliwości platformy .NET, korzystając z najlepszych funkcji .NET Core, .NET Framework, Xamarin i Mono.
- Skompiluj ten produkt z jednej bazy kodu, nad którą deweloperzy (Microsoft i społeczność) mogą pracować i rozwijać się razem, co poprawia wszystkie scenariusze.

Aby uzyskać więcej informacji na temat planowanych dla .NET 5, zobacz [Wprowadzenie do .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
