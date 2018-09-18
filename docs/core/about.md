---
title: Temat platformy .NET Core
description: Dowiedz się więcej na temat platformy .NET Core.
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.openlocfilehash: d9943246b683c8fd892e7bc5fd09a10b72e31a5f
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969712"
---
# <a name="about-net-core"></a>Temat platformy .NET Core

.NET core ma następującą charakterystykę:

- **Dla wielu platform:** działa na Windows, macOS i Linux [systemów operacyjnych](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).
- **Spójność w ramach architektury:** uruchamia kod z takie samo zachowanie na wielu architekturach, w tym x64, x86 i ARM.
- **Narzędzia wiersza polecenia:** zawiera łatwy w użyciu narzędzia wiersza polecenia, które być używane dla rozwoju lokalnych i w scenariuszach ciągłej integracji.
- **Elastyczne wdrażanie:** zainstalowany side-by-side użytkownika — lub dla komputera lub mogą być zawarte w Twojej aplikacji. Mogą być używane z [kontenerów platformy Docker](docker/index.md).
- **Zgodne:** platformy .NET Core jest zgodny z .NET Framework, Xamarin i platformy Mono, za pośrednictwem [.NET Standard](../standard/net-standard.md).
- **"Open source":** platformy .NET Core jest typu open source, przy użyciu licencji MIT i Apache 2. Platforma .NET core to [.NET Foundation](https://dotnetfoundation.org/) projektu.
- **Obsługiwane przez firmę Microsoft:** platformy .NET Core jest obsługiwane przez firmę Microsoft na [Obsługa platformy .NET Core](https://www.microsoft.com/net/core/support/).

## <a name="languages"></a>Języki

Języki C#, Visual Basic i F # może służyć do pisania aplikacji i bibliotek dla platformy .NET Core. Te języki są lub można zintegrować z tekstu edytorami i środowiskami IDE, w tym [programu Visual Studio](https://visualstudio.microsoft.com/vs/), [programu Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text i Vim. Ta integracja świadczą, w całości, to dobry osoby z [technologię OmniSharp](http://www.omnisharp.net/) i [Ionide](http://ionide.io) projektów.

## <a name="apis"></a>interfejsy API

.NET core udostępnia interfejsy API w wielu sytuacjach należy wykonać kilka z nich:

- Typy pierwotne, takie jak [bool] [ bool] i [int][int].
- Kolekcje, takie jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Typy narzędzia, takie jak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, i <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Typy danych, takich jak <xref:System.Data.DataSet?displayProperty=nameWithType>, i [DbSet][dbset].
- Typy o wysokiej wydajności, takich jak <xref:System.Numerics.Vector?displayProperty=nameWithType> i [potoki][pipelines].

.NET core zapewnia zgodność z .NET Framework oraz interfejsów API platformy Mono przez zaimplementowanie [.NET Standard](../standard/net-standard.md) specyfikacji.

[bool]: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/bool
[int]: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/int
[pipelines]: https://blogs.msdn.microsoft.com/dotnet/2018/07/09/system-io-pipelines-high-performance-io-in-net/
[dbset]: https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/

## <a name="frameworks"></a>Struktury

Wiele struktur zostały utworzone na podstawie platformy .NET Core:

- [ASP.NET Core](/aspnet/core/)
- [System Windows 10 Universal Windows Platform (systemu Windows UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Kompozycja

.NET core składa się z następujących elementów:

- [Środowisko uruchomieniowe programu .NET Core](https://github.com/dotnet/coreclr), która zapewnia system typów, z ładowaniem zestawu, moduł wyrzucania elementów bezużytecznych, współdziałanie natywne i innych podstawowych usług. [Bibliotek platformy .NET core](https://github.com/dotnet/corefx) zapewniają pierwotne typy danych, typy skład aplikacji i narzędzi podstawowych.
- [Środowisko uruchomieniowe ASP.NET](https://github.com/aspnet/home), które oferuje platforma tworzenia nowoczesnym rozwiązaniom w chmurze opartego internet połączonych aplikacji, takich jak aplikacje sieci web, aplikacji IoT oraz zapleczy aplikacji mobilnych.
- [Narzędzi interfejsu wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli) i Kompilatory języka ([Roslyn](https://github.com/dotnet/roslyn) i [F #](https://github.com/microsoft/visualfsharp)), dzięki którym Środowisko deweloperskie platformy .NET Core.
- [Narzędzia dotnet](https://github.com/dotnet/core-setup), która umożliwia uruchamianie aplikacji .NET Core i narzędzi interfejsu wiersza polecenia. Środowisko wykonawcze wybiera i hostuje środowisko wykonawcze, zapewnia zestawu zasad podczas ładowania i uruchamia aplikacje i narzędzia.

Te składniki są dystrybuowane w następujący sposób:

- [Środowisko uruchomieniowe programu .NET core](https://www.microsoft.com/net/download/dotnet-core/2.1) — zawiera biblioteki środowiska uruchomieniowego i framework .NET Core.
- [Środowisko uruchomieniowe programu ASP.NET Core](https://www.microsoft.com/net/download/dotnet-core/2.1) — zawiera biblioteki środowiska uruchomieniowego i struktury programu ASP.NET Core i .NET Core.
- [Zestaw .NET core SDK](https://www.microsoft.com/net/download/dotnet-core/2.1) — obejmuje narzędzia interfejsu wiersza polecenia platformy .NET, środowisko uruchomieniowe programu ASP.NET Core i środowisko uruchomieniowe programu .NET Core i framework.

### <a name="open-source"></a>"Open Source"

[.NET core](https://github.com/dotnet/core) jest typu open source ([licencją MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) i była przyczyniały się do [.NET Foundation](https://dotnetfoundation.org) przez firmę Microsoft w 2014 roku. Teraz jest jednym z najbardziej aktywnych projektów .NET Foundation. Może ona swobodnie przyjęta przez użytkowników indywidualnych i firm, w tym do celów osobistych, akademickich lub handlowych. Wiele firm używa platformy .NET Core, jako część aplikacji, narzędzi, nowych platform i usług hostingu. Niektóre z tych firm wprowadzić znaczny wkład do platformy .NET Core w witrynie GitHub i wytyczne dotyczące kierunek produktu jako część [grupy kierownicy w .NET Foundation technicznych](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Przeznaczony dla zdolności adaptacyjnych

.NET core został skompilowany jako bardzo podobne, ale unikatowy produkt względem innych produktów platformy .NET. Ma ona ustalono, aby umożliwić szerokiego podatność na nowe platformy i obciążeń. Ma kilka systemu operacyjnego i procesora CPU dostępnych portów i mogą być przenoszone do wielu innych.

Produkt jest dzielony na wielu części, umożliwiając z różnymi częściami dostosowania do nowych platform o różnych porach. Środowisko uruchomieniowe i podstawowe biblioteki charakterystyczne dla platformy musi być przenoszone jako jednostka. Niezależne od platformy biblioteki powinny działać jako — znajduje się na wszystkich platformach, wynikające z konstrukcji. Istnieje różnica projektu, do zmniejszenia implementacji specyficznych dla platformy w celu zwiększania wydajności dla deweloperów, preferowanie kodu C# neutralnymi zawsze wtedy, gdy algorytm lub interfejsu API może być implementowany w całości lub w ten sposób w ramach.

Osoby poproś często implementacji platformy .NET Core w celu obsługują wiele systemów operacyjnych. Poproś ich zazwyczaj Jeśli istnieją oddzielne implementacje lub [kompilacji warunkowej](https://en.wikipedia.org/wiki/Conditional_compilation) jest używany. Jest zarówno za pomocą silnych odchylenie kierunku kompilacji warunkowej.

Widoczne na wykresie poniżej większość [CoreFX](https://github.com/dotnet/corefx) jest niezależny od platformy kod, który jest udostępniany na wszystkich platformach. Kod niezależny od platformy można zaimplementować jako pojedynczy zestaw przenośny, która jest używana na wszystkich platformach.

![CoreFX: Wiersze kodu na każdą platformę](../images/corefx-platforms-loc.png)

Implementacje Windows i Unix są podobny rozmiar. Windows ma większe implementacji, ponieważ CoreFX implementuje niektóre funkcje tylko do Windows, takich jak [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , ale jeszcze nie implementuje wiele pojęć tylko do systemu Unix. Zobaczysz również, że większość implementacji systemu Linux i macOS są współdzielone w implementacji systemu Unix, podczas implementacji specyficznych dla systemu Linux i macOS są mniej więcej podobne pod względem rozmiaru.

Istnieją różne biblioteki specyficzne dla platformy i niezależny od platformy w programie .NET Core. Możesz zobaczyć wzorca w kilka przykładów:

- [CoreCLR](https://github.com/dotnet/coreclr) jest specyficzne dla platformy. Opiera się na górze podsystemów systemu operacyjnego, takich jak Menedżer pamięci i harmonogram wątku.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) i [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) są specyficzne dla platformy, biorąc pod uwagę, że magazyn i interfejsu API kryptografii różnią się w każdym systemie operacyjnym.
- [System.Collections —](https://github.com/dotnet/corefx/tree/master/src/System.Collections) i [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) są niezależne od platformy, biorąc pod uwagę, że będą oni tworzyć i pracować nad struktur danych.

## <a name="comparisons-to-other-net-implementations"></a>Porównanie z innych implementacji platformy .NET

Być może najłatwiej jest poznać wielkość i kształt platformy .NET Core, porównując ją do istniejących implementacji .NET.

### <a name="comparison-with-net-framework"></a>Porównanie z programem .NET Framework

.NET została po raz pierwszy przez firmę Microsoft w wersji 2000, a następnie ewoluował w tym miejscu. .NET Framework zostało podstawowej implementacji .NET utworzone przez firmę Microsoft, w tym okresie prawie dekadę dwa.

Najważniejsze różnice między .NET Core i .NET Framework:

- **Modele aplikacji** — .NET Core nie obsługuje wszystkich .NET Framework — modele aplikacji. W szczególności nie obsługuje, MVC i formularzy sieci Web platformy ASP.NET. Ogłoszono go, [.NET Core 3 będzie obsługiwać WPF i formularze Windows](https://blogs.msdn.microsoft.com/dotnet/2018/05/07/net-core-3-and-support-for-windows-desktop-applications/).
- **Interfejsy API** — .NET Core zawiera dużego podzbioru .NET Framework Biblioteka klasy podstawowej, przy użyciu różnych wyprowadzenie (nazwy zestawu różnią się; elementy eksponowane na typach różnią się w przypadku klucza). Te różnice wymagają zmiany portu źródłowego platformę .NET Core, w niektórych przypadkach (zobacz [dotnet/microsoft-apiport](https://github.com/microsoft/dotnet-apiport)). Implementuje platformy .NET core [.NET Standard](../standard/net-standard.md) specyfikacji interfejsu API.
- **Podsystemy** — .NET Core implementuje podzbiór podsystemów w programie .NET Framework w celu wykonania prostsze i modelu programowania. Na przykład zabezpieczenia dostępu kodu (CAS) jest nieobsługiwana, gdy odbicie jest obsługiwana.
- **Platform** — .NET Framework obsługuje Windows i Windows Server, a .NET Core obsługuje również w systemach macOS i Linux.
- **"Open Source"** — platforma .NET Core to typu open source, podczas gdy [tylko do odczytu podzestaw programu .NET Framework](https://github.com/microsoft/referencesource) jest "open source".

.NET Core jest unikatowa i ma między nimi istotne różnice w .NET Framework i inne implementacje platformy .NET, jest bardzo proste udostępnianie kodu między tych implementacji przy użyciu źródła lub binarny technik do udostępniania.

### <a name="comparison-with-mono"></a>Porównanie z platformy Mono

[Narzędzie mono](http://www.mono-project.com/) to oryginalny platform i ["open source"](https://github.com/mono/mono) implementacji .NET, najpierw w 2004 wysyłki. Go mogą być uważane za klon społeczności programu .NET Framework. Zespół projektu Mono skorzystała z otwartym [standardów .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (szczególnie 335 ECMA) opublikowane przez firmę Microsoft w celu zapewnienia zgodna implementacja.

Najważniejsze różnice między .NET Core i platformy Mono:

- **Modele aplikacji** — narzędzie Mono obsługuje podzbiór .NET Framework — modele aplikacji (na przykład Windows Forms) i niektóre z nich dodatkowe (na przykład [Xamarin.iOS](https://www.xamarin.com/platform)) za pomocą produktu Xamarin. .NET core nie obsługuje tych.
- **Interfejsy API** — obsługuje platformy Mono [dużego podzestawu](http://docs.go-mono.com/?link=root%3a%2fclasslib) .NET Framework interfejsów API, za pomocą tej samej nazwy zestawów i uwzględniając.
- **Platform** — narzędzie Mono obsługuje wiele platform i procesorów.
- **Oprogramowanie typu Open Source** — narzędzie Mono i .NET Core Użyj licencją MIT i są projektami .NET Foundation.
- **Fokus** — głównym celem Mono w ostatnich latach jest platform urządzeń przenośnych, gdy platformy .NET Core ma fokus w obciążeń typu cloud i pulpitu.
