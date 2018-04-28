---
title: Przewodnik platformy .NET Core
description: Oprogramowanie .NET core jest implementacją moduły, wysokiej wydajności platformy .NET do tworzenia aplikacji systemu Windows, Linux i komputerów Mac. Więcej informacji na temat platformy .NET Core, aby rozpocząć pracę.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: dee943a025bf4e3ad97685bde1735f0710023573
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-guide"></a>Przewodnik platformy .NET Core

> Zapoznaj się z ["Wprowadzenie" samouczki](get-started.md) Aby dowiedzieć się, jak utworzyć prostą aplikację platformy .NET Core. Potrwa to tylko kilka minut, aby uzyskać pierwszej aplikacji do pracy.

Oprogramowanie .NET core jest to platforma programistyczna ogólnego przeznaczenia, obsługiwane przez firmę Microsoft i społecznością .NET na [GitHub](https://github.com/dotnet/core). Jest między platformami, obsługi systemu Windows, system macOS i Linux i mogą być używane w osadzonych IoT scenariusze, chmury i urządzenia. 

Następujące najlepsze cechy zdefiniować .NET Core:

- **Elastyczne wdrażanie:** może być uwzględniony w aplikacji lub instalowane side-by-side użytkownika lub komputera na poziomie.
- **Obsługujący wiele platform:** działa w systemie Windows, system macOS i Linux; mogą być przenoszone do innych systemów operacyjnych. [Obsługiwanych systemów operacyjnych (OS)](https://github.com/dotnet/core/blob/master/roadmap.md), procesorów i scenariusze aplikacji będzie rosnąć wraz z upływem czasu, dostarczone przez firmę Microsoft, inne firmy i osób.
- **Narzędzia wiersza polecenia:** wszystkie scenariusze produktu może być wykonywane w wierszu polecenia. 
- **Zgodne:** .NET Core jest zgodny z .NET Framework, Xamarin i Mono, za pomocą [.NET Standard](../standard/net-standard.md).
- **Typu open source:** platformy .NET Core jest typu open source, przy użyciu MIT i Apache 2 licencji. Dokumentacja jest objęte [DW przez](https://creativecommons.org/licenses/by/4.0/). Oprogramowanie .NET core jest [.NET Foundation](https://dotnetfoundation.org/) projektu.
- **Obsługiwane przez firmę Microsoft:** .NET Core jest obsługiwana przez firmę Microsoft, na [Obsługa .NET Core](https://www.microsoft.com/net/core/support/)

## <a name="composition"></a>Kompozycja

Oprogramowanie .NET core składa się z następujących elementów:

- A [środowiska uruchomieniowego .NET](https://github.com/dotnet/coreclr), który zapewnia system typów, ładowania zestawu, moduł Garbage Collector, interop macierzystego i innych podstawowych usług. 
- Zestaw [bibliotek platformy](https://github.com/dotnet/corefx), które zapewniają typy pierwotne, typy kompozycji aplikacji i podstawowe narzędzia. 
- A [zestawu SDK narzędzia](https://github.com/dotnet/cli) i [Kompilatory języka](https://github.com/dotnet/roslyn) umożliwiających środowisko dewelopera podstawowej, dostępne w [.NET Core SDK](sdk.md).
- Host aplikacji "dotnet", który jest używany do uruchamiania aplikacji .NET Core. Wybiera środowiska uruchomieniowego i obsługuje środowisko uruchomieniowe, udostępnia zestaw ładowania zasady i uruchamia aplikację. Tym samym hoście służy również do uruchamiania narzędzia zestawu SDK w podobny sposób.

### <a name="languages"></a>Języki

Języki C#, VB i F # mogą służyć do pisania aplikacji i bibliotek dla platformy .NET Core. Kompilatory Uruchom na .NET Core, umożliwiając tworzenie dla platformy .NET Core w dowolnym miejscu go uruchamia. Ogólnie rzecz biorąc nie będzie używany kompilatory bezpośrednio, ale pośrednio przy użyciu narzędzia zestawu SDK.

Kompilatory języka C#, VB i F # i narzędzi platformy .NET Core są lub można zintegrować różne edytory tekstów i IDEs, łącznie z programu Visual Studio, [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text i Vim wprowadzania programowania .NET Core dostępną opcją w sieci ulubiony element kodowania środowiska i systemu operacyjnego. Integracja ta zostanie podany, w części przez dobrej pracowników z [projektu OmniSharp](http://www.omnisharp.net/).

### <a name="net-apis-and-compatibility"></a>Interfejsów API architektury .NET i zgodności

Oprogramowanie .NET core można traktować jako wersja platformy .NET w warstwie programu .NET Framework podstawowej klasy biblioteki (BCL) i platform. Implementuje [.NET Standard](../standard/net-standard.md) specyfikacji. Oprogramowanie .NET core zawiera podzestawu interfejsów API, które są dostępne w programie .NET Framework lub Mono/Xamarin. W niektórych przypadkach typy nie są pełni zaimplementowane (niektóre elementy nie są dostępne lub została przeniesiona).

Przyjrzyj się [plan .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md) Aby dowiedzieć się więcej na temat plan interfejsu API programu .NET Core.

### <a name="relationship-to-net-standard"></a>Relacja do platformy .NET Standard

[.NET Standard](../standard/net-standard.md) to specyfikacja interfejsu API, opisujący spójny zestaw interfejsów API architektury .NET, który deweloperzy mogą oczekiwać w każdej implementacji .NET. Implementacje .NET należy zaimplementować tej specyfikacji celu uznany za zgodnego .NET Standard i obsługuje bibliotek przeznaczonych .NET Standard. 

Oprogramowanie .NET core implementuje standardowe .NET i w związku z tym obsługuje bibliotek .NET Standard.

### <a name="workloads"></a>Pakiety robocze

Samodzielnie .NET Core zawiera model pojedynczej aplikacji — aplikacje konsoli — co jest przydatne dla narzędzi, usług lokalnych i gry tekstowych. Modele dodatkowych aplikacji zostały utworzone na podstawie .NET Core do rozszerzenia jego funkcji, takich jak:

- [ASP.NET Core](/aspnet/core/)
- [Platforma uniwersalna systemu Windows 10 systemu Windows (UWP)](https://developer.microsoft.com/windows)
- [Platformy Xamarin.Forms przy przeznaczonych dla platformy uniwersalnej systemu Windows](https://www.xamarin.com/forms)

### <a name="open-source"></a>Typu Open Source

[Oprogramowanie .NET core](https://github.com/dotnet/core) jest typu open source (licencja MIT) i został przyczyniły się do [.NET Foundation](https://dotnetfoundation.org) przez firmę Microsoft w 2014 r. Teraz jest jednym z najbardziej aktywnych projektów .NET Foundation. Może ona za darmo przyjęta przez osoby i firm, w tym do celów osobistych, academic lub handlowych. Wiele firm Użyj .NET Core jako część aplikacji, narzędzia i nowe platformy usług hostingu. Niektóre z tych firm dokonać znaczących wkładów .NET Core w serwisie GitHub i wytyczne dotyczące kierunku produktu w ramach [grupy kierownicy w .NET Foundation technicznych](https://dotnetfoundation.org/blog/tsg-welcome).

## <a name="acquisition"></a>Nabycia

Oprogramowanie .NET core jest dystrybuowane w dwie główne metody jako pakietów na NuGet.org i jako autonomiczny dystrybucji.

### <a name="distributions"></a>Dystrybucje

Możesz pobrać oprogramowanie .NET Core w [.NET Core wprowadzenie](https://www.microsoft.com/net/core) strony.

- *Microsoft .NET Core* dystrybucji obejmuje środowiska uruchomieniowego środowisko CoreCLR, skojarzone biblioteki, host aplikacji konsoli i `dotnet` uruchamiania aplikacji. Jest opisany przez [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) metapackage.
- *Microsoft .NET Core SDK* dystrybucji obejmuje oprogramowanie .NET Core i zestaw narzędzi do przywracania pakietów NuGet i kompilowania i tworzenia aplikacji. 

Zwykle najpierw zostanie zainstalowany .NET Core SDK, aby rozpocząć programowanie .NET Core. Można zainstalować dodatkowe oprogramowanie .NET Core (np. wersja wstępna) kompilacji.

### <a name="packages"></a>Pakiety

- [.NET core pakiety](packages.md) zawierają środowiska uruchomieniowego .NET Core i bibliotek (implementacji i zestawy referencyjne). Na przykład [System.Net.Http](https://www.nuget.org/packages/System.Net.Http/).
- [.NET core Metapackages](packages.md) opisano różne warstwy i modeli aplikacji za pomocą odwołań do odpowiedniego zbioru pakiety bibliotekę numerów wersji.

## <a name="architecture"></a>Architektura

Oprogramowanie .NET core jest implementacją .NET i platform. Główne obawy architektury unikatowe dla platformy .NET Core są związane z dostarczanie implementacje specyficzne dla platformy dla obsługiwanych platform.

### <a name="environments"></a>Środowisk

Oprogramowanie .NET core jest obsługiwana przez firmę Microsoft w systemie Windows, system macOS i Linux. W systemie Linux firma Microsoft obsługuje głównie .NET Core w systemie Red Hat Enterprise Linux (RHEL) oraz Debian dystrybucji rodziny.

Oprogramowanie .NET core obsługuje obecnie X64 procesorów. W systemie Windows obsługiwane jest również X86. ARM64 i ARM32 są w toku.

[.NET Core plan](https://github.com/dotnet/core/blob/master/roadmap.md) zawiera bardziej szczegółowe informacje dotyczące obciążenia i obsługa środowiska systemu operacyjnego i procesora CPU i planów.

Innych firm lub grup może obsługiwać inne typy aplikacji i środowiska .NET Core.

### <a name="designed-for-adaptability"></a>Przeznaczone dla zdolności adaptacyjnych

Oprogramowanie .NET core został skompilowany jako produkt bardzo podobne, lecz unikatowe względem innych produktów platformy .NET. Został zaprojektowany umożliwiające szerokie podatność na nowe platformy, dla nowych obciążeń i z nowego toolchains kompilatora. Ma kilka systemu operacyjnego i procesora CPU portów w toku i mogą być przenoszone do wielu innych. Na przykład [LLILC](https://github.com/dotnet/llilc) projektu, który jest wczesne prototypu natywnej kompilacji dla platformy .NET Core za pomocą [LLVM](http://llvm.org/) kompilatora.

Produkt jest dzielony na wielu części, włączanie różnych części należy dostosować do nowych platform na różne harmonogramy. Środowisko wykonawcze i bibliotek podstawowych specyficzne dla platformy musi być przenoszone jako jednostka. Niezależne od platformy bibliotek powinny działać jako — znajduje się na wszystkich platformach przez konstrukcji. Brak odchylenia projektu, do zmniejszenia implementacje specyficzne dla platformy, aby zwiększyć wydajność deweloperów, preferowanie niezależny od platformy C# kod zawsze, gdy algorytm lub interfejsu API można zaimplementować w całości lub w części w ten sposób.

Osoby poproś często, jak .NET Core jest zaimplementowana w celu zapewnienia obsługi wielu systemów operacyjnych. Zwykle został poproszony o Jeśli istnieją oddzielne implementacje lub [kompilacja warunkowa](https://en.wikipedia.org/wiki/Conditional_compilation) jest używany. Jest zarówno z Silne odchylenia do kompilacji warunkowej.

Widać na wykresie poniżej większość [CoreFX](https://github.com/dotnet/corefx) jest kod niezależny od platformy, który jest udostępniany na wszystkich platformach. Kod o neutralnym poziomie platformy można zaimplementować jako pojedynczego zestawu przenośny, który jest używany na wszystkich platformach.

![CoreFX: Wierszy kodu dla każdej platformy](../images/corefx-platforms-loc.png)

Wdrożenia systemu Windows i Unix są podobne w rozmiarze. System Windows ma większe implementacji, ponieważ CoreFX implementuje niektórych funkcji systemu Windows, takich jak [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) , ale nie implementuje jeszcze żadnych koncepcji tylko do systemu Unix. Widoczne będzie także, że większość wdrożeń systemów Linux i macOS są współużytkowane przez implementacji systemu Unix, podczas implementacji specyficznych dla systemu Linux i macOS grubsza podobny rozmiar.


Brak kombinacji bibliotek niezależny od platformy i specyficzne dla platformy .NET Core. Można wyświetlić wzorca w kilka przykładów:

- [Środowisko CoreCLR](https://github.com/dotnet/coreclr) jest specyficzne dla platformy. Korzysta z wbudowanej w języku C/C++, dlatego jest specyficzne dla platformy przez konstrukcji.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) i [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) są specyficzne dla platformy, biorąc pod uwagę, że magazyn i cryptography API różnią się znacznie w każdego systemu operacyjnego. 
- [System.Collections —](https://github.com/dotnet/corefx/tree/master/src/System.Collections) i [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) jest niezależny od platformy, biorąc pod uwagę, że tworzenie i działa za pośrednictwem struktury danych.

## <a name="comparisons-to-other-net-implementations"></a>Porównanie z innych implementacji .NET

Być może jest łatwiej zrozumieć wielkość i kształt .NET Core przez porównanie z istniejącymi implementacjami .NET. 

### <a name="comparison-with-net-framework"></a>Porównanie z .NET Framework

Najpierw anonsowane przez firmę Microsoft w wersji 2000 .NET, a następnie ewoluował stamtąd. .NET Framework został podstawowej implementacji .NET produkowane przez firmę Microsoft podczas tego zakresu 15 + roku. 

Najważniejsze różnice między .NET Core i .NET Framework: 

- **Modele aplikacji** --.NET Core nie obsługuje wszystkie .NET Framework app modele, w części ponieważ wiele z nich jest oparty na technologii systemu Windows, takich jak WPF (oparty na technologii DirectX). Konsola i modeli aplikacji platformy ASP.NET Core są obsługiwane przez oprogramowanie .NET Core i .NET Framework. 
- **Interfejsy API** --.NET Core zawiera wiele takich samych, ale mniej interfejsy API programu .NET Framework i z różnych factoring (nazwy zestawu są różne; kształtu typu różni się w przypadku klucza). Te różnice obecnie zwykle wymagają zmiany portu źródła .NET Core. Implementuje .NET core [.NET Standard](../standard/net-standard.md) interfejsu API, który będzie rosnąć uwzględnienie z interfejsu API programu .NET Framework BCL wraz z upływem czasu.
- **Podsystemy** --.NET Core implementuje podzbiór podsystemów w programie .NET Framework w celu implementacji prostszy i modelu programowania. Na przykład zabezpieczenia dostępu kodu (CAS) jest nieobsługiwana, gdy odbicia jest obsługiwana.
- **Platformy** — program .NET Framework obsługuje system Windows i Windows Server, a oprogramowanie .NET Core obsługuje również system macOS i Linux.
- **Open Source** — .NET Core jest typu open source, podczas gdy [tylko do odczytu podzbiór programu .NET Framework](https://github.com/microsoft/referencesource) jest typu open source.

Oprogramowanie .NET Core jest unikatowa, i ma istotne różnice do programu .NET Framework oraz inne implementacje .NET, jest proste udostępnianie kodu przy użyciu źródła lub binarne techniki udostępniania. 

### <a name="comparison-with-mono"></a>Porównanie z Mono

[Mono](http://www.mono-project.com/) to oryginalna platform i [typu open source](https://github.com/mono/mono) implementacji .NET, najpierw w 2004 wysyłki. Go można traktować jako klon społeczności programu .NET Framework. Zespół projektu Mono zależał od Otwórz [standardów .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (szczególnie 335 ECMA) opublikowane przez firmę Microsoft w celu implementacji zgodne.

Główne różnice między .NET Core i Mono:

- **Modele aplikacji** — Mono obsługuje podzbiór aplikacji .NET Framework — modele (na przykład formularze systemu Windows) i niektóre z nich dodatkowych (na przykład [Xamarin.iOS](https://www.xamarin.com/platform)) za pomocą platformy Xamarin produktu. Oprogramowanie .NET core nie obsługuje te.
- **Interfejsy API** — obsługuje Mono [dużego podzestawu](http://docs.go-mono.com/?link=root%3a%2fclasslib) .NET Framework interfejsów API, przy użyciu tej samej nazwy zestawu i factoring.
- **Platformy** --Mono obsługuje wiele platform i procesorów.
- **Open Source** --Mono i .NET Core użyć licencji MIT i projektów .NET Foundation.
- **Fokus** — podstawowy Mono w ostatnich latach koncentruje się platform urządzeń przenośnych, gdy oprogramowanie .NET Core koncentruje się na obciążeń chmury.
