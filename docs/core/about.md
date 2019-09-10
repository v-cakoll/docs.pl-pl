---
title: Informacje o platformie .NET Core
description: Dowiedz się więcej o programie .NET Core.
author: richlander
ms.date: 08/01/2018
ms.openlocfilehash: ea9253bacf2bcee63430cd45f2a9ed412ce629e7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849139"
---
# <a name="about-net-core"></a>Informacje o platformie .NET Core

Platforma .NET Core ma następujące cechy:

- **Na wielu platformach:** Działa w [systemach operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS i Linux.
- **Spójne między architekturami:** Uruchamia kod z zachowaniem tego samego zachowania w wielu architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:**  Obejmuje łatwe w użyciu narzędzia wiersza polecenia, które mogą być używane do lokalnego programowania i w scenariuszach ciągłej integracji.
- **Elastyczne wdrożenie:** Mogą być dołączane do aplikacji lub instalowane obok siebie (instalacje dla całego użytkownika lub systemu). Może być używany z [kontenerami platformy Docker](docker/index.md).
- **Zgodne:** program .NET Core jest zgodny z .NET Framework, Xamarin i mono, za pośrednictwem [.NET Standard](../standard/net-standard.md).
- **Open Source:** Platforma .NET Core jest platformą Open Source, przy użyciu licencji MIT i Apache 2. .NET Core to projekt [platformy .NET Foundation](https://dotnetfoundation.org/) .
- **Obsługiwane przez firmę Microsoft:** platforma .NET Core jest obsługiwana przez firmę Microsoft w ramach [pomocy technicznej dla platformy .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Języki

C#, Visual Basic i F# języki mogą służyć do pisania aplikacji i bibliotek dla platformy .NET Core. Te języki są lub można zintegrować z ulubionymi edytorami tekstu i środowisk IDE, takimi jak [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), text-limonowe i vim. Ta integracja jest świadczona w części przez dobrą osób z projektów [OmniSharp](https://www.omnisharp.net/) i [Ionide](http://ionide.io) .

## <a name="apis"></a>interfejsy API

Platforma .NET Core udostępnia interfejsy API dla wielu scenariuszy, a kilka z nich jest następujących:

- Typy pierwotne, takie jak [bool](../csharp/language-reference/keywords/bool.md) i [int](../csharp/language-reference/builtin-types/integral-numeric-types.md).
- Kolekcje, takie jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Typy narzędzi, takie jak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, i <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Typy danych, takie jak <xref:System.Data.DataSet?displayProperty=nameWithType>i [nieogólnymi](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Typy wysokiej wydajności, takie jak <xref:System.Numerics.Vector?displayProperty=nameWithType> [potoki](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/).

Platforma .NET Core zapewnia zgodność z interfejsami API .NET Framework i mono, implementując specyfikację [.NET Standard](../standard/net-standard.md) .

## <a name="frameworks"></a>Struktury

W oparciu o platformę .NET Core zostały utworzone wiele platform:

- [ASP.NET Core](/aspnet/core/)
- [Platforma uniwersalna systemu Windows systemu Windows 10 (platformy UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Budowa

Platforma .NET Core składa się z następujących części:

- [Środowisko uruchomieniowe platformy .NET Core](https://github.com/dotnet/coreclr), które udostępnia system typów, ładowanie zestawu, Moduł wyrzucania elementów bezużytecznych, natywną międzyoperacyjność i inne podstawowe usługi. [Biblioteki .NET Core Framework](https://github.com/dotnet/corefx) zapewniają typy danych pierwotnych, typy kompozycji aplikacji i podstawowe narzędzia.
- [Środowisko uruchomieniowe ASP.NET](https://github.com/aspnet/home), które zapewnia platformę do tworzenia nowoczesnych aplikacji internetowych opartych na chmurze, takich jak aplikacje internetowe, aplikacje IoT i frontony mobilne.
- [Narzędzia interfejs wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli) i kompilatory języka ([Roslyn](https://github.com/dotnet/roslyn) i [F#](https://github.com/microsoft/visualfsharp)), które umożliwiają środowisko deweloperskie platformy .NET Core.
- [Narzędzie dotnet](https://github.com/dotnet/core-setup), które służy do uruchamiania aplikacji .NET Core i narzędzi interfejsu wiersza polecenia. Wybiera środowisko uruchomieniowe i hostuje środowisko uruchomieniowe, udostępnia zasady ładowania zestawu i uruchamia aplikacje i narzędzia.

Te składniki są dystrybuowane w następujący sposób:

- [Środowisko uruchomieniowe platformy .NET Core](https://dotnet.microsoft.com/download) — obejmuje środowisko uruchomieniowe programu .NET Core i biblioteki struktury.
- [Środowisko uruchomieniowe ASP.NET Core](https://dotnet.microsoft.com/download) — obejmuje ASP.NET Core i środowisko uruchomieniowe platformy .NET Core oraz biblioteki struktury.
- [Zestaw .NET Core SDK](https://dotnet.microsoft.com/download) — obejmuje narzędzia interfejsu wiersza polecenia platformy .NET, środowisko uruchomieniowe ASP.NET Core i środowisko uruchomieniowe platformy .NET Core.

### <a name="open-source"></a>Kod open source

[.NET Core](https://github.com/dotnet/core) to Open Source ([licencja mit](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) i była współautorem programu [.NET Foundation](https://dotnetfoundation.org) przez firmę Microsoft w 2014. Jest to teraz jeden z najbardziej aktywnych projektów programu .NET Foundation. Mogą być swobodnie wprowadzane przez osoby i firmy, w tym w celach indywidualnych, akademickich i komercyjnych. Wiele firm używa platformy .NET Core jako części aplikacji, narzędzi, nowych platform i usług hostingowych. Niektóre z tych firm czynią znaczące wkłady do programu .NET Core w witrynie GitHub i zapewniają wskazówki dotyczące kierunku produktu w ramach [grupy sterowania technicznego .NET Foundation](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Zaprojektowana na potrzeby adaptacji

Platforma .NET Core została skompilowana jako bardzo podobny, ale unikatowy produkt względem innych produktów .NET. Została zaprojektowana tak, aby umożliwić szeroką adaptację do nowych platform i obciążeń. Dostępne są różne porty systemu operacyjnego i procesora CPU, które można przenieść do wielu innych.

Produkt jest podzielony na kilka części, dzięki czemu różne części można dostosować do nowych platform w różnym czasie. Biblioteki podstawowe dla środowiska uruchomieniowego i specyficznego dla platformy muszą być portami jednostkowymi. Biblioteki platform-niezależny od powinny funkcjonować tak, jak na wszystkich platformach, przez konstrukcję. Istnieje różnica projektu umożliwiająca zredukowanie implementacji specyficznych dla platformy w celu zwiększenia wydajności dla deweloperów i wstępnego nałożenia kodu neutralnego C# na platformę, za każdym razem, gdy algorytm lub interfejs API można zaimplementować w pełni lub w ten sposób.

Ludzie często pytają, w jaki sposób platforma .NET Core jest zaimplementowana w celu obsługi wielu systemów operacyjnych. Zazwyczaj pytają, czy istnieją oddzielne implementacje lub kiedy jest używana [Kompilacja warunkowa](https://en.wikipedia.org/wiki/Conditional_compilation) . Jest to zarówno, jak i silna różnica w stosunku do kompilacji warunkowej.

Na poniższym wykresie można zobaczyć, że większość [CoreFX](https://github.com/dotnet/corefx) jest kodem niezależnym od platformy, który jest udostępniany na wszystkich platformach. Kod neutralny dla platformy można zaimplementować jako pojedynczy zestaw przenośny, który jest używany na wszystkich platformach.

![CoreFX: Wiersze kodu na platformę](../images/corefx-platforms-loc.png)

Implementacje systemów Windows i UNIX mają podobne rozmiary. System Windows ma większą implementację, ponieważ CoreFX implementuje niektóre funkcje tylko dla systemu Windows, takie jak [Microsoft. Win32. Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , ale nie implementuje jeszcze wielu koncepcji tylko dla systemu UNIX. Zobaczysz również, że większość implementacji systemów Linux i macOS jest współdzielona przez implementację systemu UNIX, podczas gdy implementacje specyficzne dla komputerów z systemem Linux i macOS są w przybliżeniu podobne do wielkości.

W programie .NET Core istnieją różne biblioteki zależne od platformy i platformy. Wzorzec można zobaczyć w kilku przykładach:

- [CoreCLR](https://github.com/dotnet/coreclr) jest specyficzna dla platformy. Jest ona oparta na podsystemach systemu operacyjnego, takich jak Menedżer pamięci i harmonogram wątków.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) i [System. Security. Cryptography. algorytmy](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) są specyficzne dla platformy, przy czym interfejsy API magazynu i kryptografii są różne w poszczególnych systemach operacyjnych.
- [System. Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) i [System. LINQ](https://github.com/dotnet/corefx/tree/master/src/System.Linq) są niezależne od platformy, co oznacza, że tworzą i pracują ze strukturami danych.

## <a name="comparisons-to-other-net-implementations"></a>Porównania z innymi implementacjami platformy .NET

Prawdopodobnie najłatwiej zrozumieć rozmiar i kształt platformy .NET Core, porównując ją z istniejącymi implementacjami platformy .NET.

### <a name="comparison-with-net-framework"></a>Porównanie z .NET Framework

.NET został po raz pierwszy ogłoszony przez firmę Microsoft w 2000, a następnie rozwijający się z tego miejsca. .NET Framework była podstawową implementacją platformy .NET utworzoną przez firmę Microsoft w ciągu niemal dwóch okresów dekady.

Główne różnice między programami .NET Core i .NET Framework:

- **Modele aplikacji** --. .NET Core nie obsługują wszystkich modeli aplikacji .NET Framework. W szczególności nie obsługuje on ASP.NET Web Forms i ASP.NET MVC, ale obsługuje ASP.NET Core MVC. Zostało ogłoszone, że program [.NET Core 3 będzie OBSŁUGIWAŁ WPF i Windows Forms](https://devblogs.microsoft.com/dotnet/net-core-3-and-support-for-windows-desktop-applications/).
- **Interfejsy api** --. .NET Core zawierają duży podzestaw .NET Framework biblioteki klas bazowych, z różnymi współczynnikami (nazwy zestawów są różne; składowe uwidocznione w przypadku typów różnią się w kluczowych przypadkach). Różnice te wymagają zmian w źródle portów do programu .NET Core w niektórych przypadkach (zobacz [Microsoft/dotnet-apiport](https://github.com/microsoft/dotnet-apiport)). Platforma .NET Core implementuje specyfikację interfejsu API [.NET Standard](../standard/net-standard.md) .
- **Podsystemy** --. NET Core implementuje podzestaw podsystemów w .NET Framework, z celem prostszej implementacji i modelu programowania. Na przykład zabezpieczenia dostępu kodu (CAS) nie są obsługiwane, a odbicie jest obsługiwane.
- **Platformy** — .NET Framework obsługuje systemy Windows i Windows Server, podczas gdy program .NET Core obsługuje także MacOS i Linux.
- " **Open source** --. .NET Core to" open source ", podczas gdy [podzestaw tylko do odczytu .NET Framework](https://github.com/microsoft/referencesource) jest typu open source.

Podczas gdy program .NET Core jest unikatowy i ma znaczące różnice dotyczące .NET Framework i innych implementacji platformy .NET, bezpośrednie udostępnianie kodu między tymi implementacjami odbywa się przy użyciu metod udostępniania źródłowego lub binarnego.

Ponieważ .NET Core obsługuje instalację równoczesną, a jej środowisko uruchomieniowe jest całkowicie niezależne od .NET Framework, można je zainstalować na maszynach z zainstalowanym .NET Framework bez żadnych problemów.

### <a name="comparison-with-mono"></a>Porównanie z mono

[Mono](https://www.mono-project.com/) to oryginalna implementacja platformy .NET dla wielu platform i technologii [Open Source](https://github.com/mono/mono) , najpierw wysyłka w 2004. Można to traktować jako klony społeczności .NET Framework. Zespół projektu mono opiera się na otwartych [standardach .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (zwłaszcza w języku ECMA 335) publikowanych przez firmę Microsoft w celu zapewnienia zgodnej implementacji.

Główne różnice między programami .NET Core i mono:

- **Modele aplikacji** — mono obsługuje podzestaw modeli aplikacji .NET Framework (na przykład Windows Forms) i niektórych dodatkowych (na przykład [Xamarin. iOS](https://www.xamarin.com/platform)) za pomocą produktu Xamarin. Platforma .NET Core nie obsługuje tych funkcji.
- **Interfejsy API** — mono obsługuje [duże podzbiór](http://docs.go-mono.com/?link=root%3a%2fclasslib) .NET Framework interfejsów API przy użyciu tych samych nazw zestawów i ich refaktoryzacji.
- **Platformy** — mono obsługuje wiele platform i procesorów.
- **Open Source** — programy mono i .NET Core używają licencji MIT oraz projektów programu .NET Foundation.
- **Fokus** — głównym fokusem mono w ostatnich latach są platformy mobilne, natomiast platforma .NET Core koncentruje się na obciążeniach w chmurze i komputerach stacjonarnych.
