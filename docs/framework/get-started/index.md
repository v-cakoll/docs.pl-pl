---
title: Wprowadzenie do programu .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: cd27f2fb893def9e186504cc9973bae71473f005
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248911"
---
# <a name="get-started-with-net-framework"></a>Wprowadzenie do programu .NET Framework

.NET Framework to środowisko wykonywania w czasie wykonywania, które zarządza aplikacjami docelowymi .NET Framework. Składa się ze wspólnego środowiska wykonawczego języka, który zapewnia zarządzanie pamięcią i inne usługi systemowe oraz obszerną bibliotekę klas, która umożliwia programistom korzystanie z niezawodnego, niezawodnego kodu dla wszystkich głównych obszarów tworzenia aplikacji.

> [!NOTE]
> Program .NET Framework jest dostępny tylko w systemach Windows. Za pomocą [platformy .NET Core](../../core/index.md) można tworzyć i uruchamiać aplikacje w systemach Windows, MacOS i Linux.

## <a name="what-is-net-framework"></a>Co to jest .NET Framework?

.NET Framework jest zarządzanym środowiskiem wykonywania dla systemu Windows, które zapewnia wiele usług dla uruchomionych aplikacji. Składa się z dwóch głównych składników: środowiska wykonawczego języka wspólnego (CLR), który jest aparat wykonywania, który obsługuje uruchomione aplikacje i .NET Framework Class Library, która zawiera bibliotekę testowanego kodu wielokrotnego wyboru, który deweloperzy mogą wywołać z własnych aplikacji. Usługi, które program .NET Framework udostępnia uruchomionym aplikacjom, są następujące:

- Zarządzanie pamięcią. W wielu językach programowania programiści są odpowiedzialni za przydzielanie i zwalnianie pamięci oraz obsługę okresów istnienia obiektów. W aplikacjach .NET Framework program CLR udostępnia te usługi w imieniu aplikacji.

- Wspólny system typów. W tradycyjnych językach programowania podstawowe typy są definiowane przez kompilator, co komplikuje współdziałanie między językami. W .NET Framework typy podstawowe są definiowane przez system typu .NET Framework i są wspólne dla wszystkich języków docelowych .NET Framework.

- Obszerna biblioteka klas. Zamiast zapisywać ogromne ilości kodu do obsługi typowych operacji programowania niskiego poziomu, programiści używają łatwo dostępnej biblioteki typów i ich członków z biblioteki klas .NET Framework.

- Ramy rozwoju i technologie. Program .NET Framework zawiera biblioteki dla określonych obszarów tworzenia aplikacji, takich jak ASP.NET dla aplikacji sieci Web, ADO.NET dostępu do danych, Program Windows Communication Foundation dla aplikacji zorientowanych na usługi oraz program Windows Presentation Foundation dla aplikacji klasycznych systemu Windows.

- Interoperacyjność języka. Kompilatory języka, które są przeznaczone dla platformy .NET Framework emitują pośredni kod o nazwie Common Intermediate Language (CIL), który z kolei jest kompilowany w czasie wykonywania przez środowisko wykonawcze języka wspólnego. Dzięki tej funkcji procedury napisane w jednym języku są dostępne dla innych języków, a programiści koncentrują się na tworzeniu aplikacji w preferowanych językach.

- Zgodność wersji. Z rzadkimi wyjątkami aplikacje, które są opracowywane przy użyciu określonej wersji programu .NET Framework są uruchamiane bez modyfikacji w nowszej wersji.

- Wykonanie obok siebie. Program .NET Framework pomaga rozwiązywać konflikty wersji, zezwalając na istnienie wielu wersji środowiska wykonawczego języka wspólnego na tym samym komputerze. Oznacza to, że wiele wersji aplikacji może współistnieć i że aplikacja może działać w wersji programu .NET Framework, z którą została zbudowana. Wykonanie obok siebie ma zastosowanie do grup wersji programu .NET Framework 1.0/1.1, 2.0/3.0/3.5 i 4/4.5.x/4.6.x/4.7.x/4.8.

- Multitargeting. Kierując na [stronę .NET Standard,](../../standard/net-standard.md)deweloperzy tworzą biblioteki klas, które działają na wielu platformach platformy .NET Framework obsługiwanych przez tę wersję standardu. Na przykład biblioteki przeznaczone dla platformy .NET Standard 2.0 mogą być używane przez aplikacje przeznaczone dla platformy .NET Framework 4.6.1, .NET Core 2.0 i platformy uniwersalnej systemu Windows 10.0.16299.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>.NET Framework dla użytkowników

Jeśli nie opracujesz aplikacji .NET Framework, ale z nich korzystasz, nie musisz mieć określonej wiedzy na temat programu .NET Framework lub jego działania. W przeważającej części struktura jest całkowicie przejrzysta dla użytkowników.

Jeśli używasz systemu operacyjnego Windows, program .NET Framework może być już zainstalowany na komputerze. Ponadto jeśli zainstalujesz aplikację, która wymaga programu .NET Framework, program instalacyjny aplikacji może zainstalować określoną wersję struktury na komputerze. W niektórych przypadkach może zostać wyświetlone okno dialogowe z prośbą o zainstalowanie programu .NET Framework. Jeśli po wyświetleniu tego okna dialogowego i jeśli komputer ma dostęp do Internetu, spróbuj uruchomić aplikację i jeśli komputer ma dostęp do Internetu, możesz przejść do strony sieci Web, która umożliwia zainstalowanie brakującej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [Podręcznik instalacji](../install/index.md).

Ogólnie rzecz biorąc nie należy odinstalowywać wersji programu .NET Framework zainstalowanych na komputerze. Istnieją dwa powody takiego działania:

- Jeśli używana aplikacja zależy od określonej wersji programu .NET Framework, ta aplikacja może zostać przerwana, jeśli ta wersja zostanie usunięta.

- Niektóre wersje programu .NET Framework są aktualizacjami w miejscu wcześniejszych wersji. Na przykład .NET Framework 3.5 jest aktualizacją w miejscu do wersji 2.0 i .NET Framework 4.8 jest aktualizacją w miejscu do wersji 4 do 4.7.2. Aby uzyskać więcej informacji, zobacz [.NET Framework Versions and Dependencies](../migration-guide/versions-and-dependencies.md).

W wersjach systemu Windows przed systemem Windows 8, jeśli zdecydujesz się usunąć program .NET Framework, zawsze **używaj programów i funkcji** z Panelu sterowania, aby go odinstalować. Nigdy nie usuwaj wersji programu .NET Framework ręcznie. W systemie Windows 8 lub powyżej program .NET Framework jest składnikiem systemu operacyjnego i nie można go odinstalować niezależnie.

Wiele wersji programu .NET Framework może współistnieć na jednym komputerze w tym samym czasie. Oznacza to, że nie trzeba odinstalowywać poprzednich wersji, aby zainstalować nowszą wersję.

## <a name="net-framework-for-developers"></a>.NET Framework dla deweloperów

Jeśli jesteś deweloperem, wybierz dowolny język programowania, który obsługuje program .NET Framework, aby utworzyć aplikacje. Ponieważ program .NET Framework zapewnia niezależność i współdziałanie języka, współdziałasz z innymi aplikacjami i składnikami programu .NET Framework, niezależnie od języka, z którym zostały opracowane.

Aby opracować aplikacje lub składniki programu .NET Framework, wykonaj następujące czynności:

1. Jeśli nie jest preinstalowany w systemie operacyjnym, zainstaluj wersję programu .NET Framework, która będzie kierowana przez aplikację. Najnowszą wersją produkcyjną jest .NET Framework 4.8. Jest preinstalowany w systemie Windows 10 May 2019 Update i jest dostępny do pobrania we wcześniejszych wersjach systemu operacyjnego Windows. Aby zapoznać się z wymaganiami systemowymi programu .NET Framework, zobacz [Wymagania systemowe](system-requirements.md). Aby uzyskać informacje na temat instalowania innych wersji programu .NET Framework, zobacz [Podręcznik instalacji](../install/guide-for-developers.md). Dodatkowe pakiety .NET Framework są wydawane poza pasmem, co oznacza, że są one wydawane na zasadzie stopniowej poza dowolnym regularnym lub zaplanowanym cyklem wydawniczym. Aby uzyskać informacje o tych pakietach, zobacz [.NET Framework i Out-of-Band Releases](the-net-framework-and-out-of-band-releases.md).

2. Wybierz język lub języki obsługiwane przez wersję programu .NET Framework, której zamierzasz używać do tworzenia aplikacji. Dostępnych jest wiele języków, w tym [Visual Basic,](../../visual-basic/index.yml) [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml)i [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) firmy Microsoft. (Język programowania, który umożliwia tworzenie aplikacji dla platformy .NET Framework jest zgodny [ze specyfikacją wspólnej infrastruktury językowej (CLI).](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)

3. Wybierz i zainstaluj środowisko programistyczne, które będzie używane do tworzenia aplikacji i które obsługuje wybrany język programowania lub języki. Zintegrowane środowisko programistyczne firmy Microsoft (IDE) dla aplikacji .NET Framework to [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Jest dostępny w wielu edycjach.

Aby uzyskać więcej informacji na temat tworzenia aplikacji przeznaczonych dla platformy .NET Framework, zobacz [Przewodnik rozwoju](../development-guide.md).

## <a name="related-articles"></a>Pokrewne artykuły:

| Tytuł | Opis |
| ----- |------------ |
| [Przegląd](overview.md) | Zawiera szczegółowe informacje dla deweloperów, którzy budują aplikacje docelowe .NET Framework. |
| [Przewodnik instalacji](../install/index.md) | Zawiera informacje dotyczące instalowania programu .NET Framework. |  
| [Wersje .NET Framework i Out-of-Band](the-net-framework-and-out-of-band-releases.md) | W tym artykule opisano wersje poza pasmem .NET Framework i sposób ich używania w aplikacji. |
| [Wymagania systemowe](system-requirements.md) | Wyświetla listę wymagań sprzętowych i programowych dotyczących uruchamiania programu .NET Framework. |
| [Oprogramowanie .NET Core i Open-Source](net-core-and-open-source.md) | W tym artykule opisano program .NET Core w odniesieniu do programu .NET Framework i sposobu uzyskiwania dostępu do projektów typu open source .NET Core. |
| [Dokumentacja .NET Core](../../core/index.md) | Zawiera dokumentację referencyjną koncepcyjnej i interfejsu API dla platformy .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | W tym artykule omówiono .NET Standard, specyfikacji wersji, że poszczególne implementacje platformy .NET obsługuje, aby zagwarantować, że spójny zestaw interfejsów API jest dostępny na wielu platformach.

## <a name="see-also"></a>Zobacz też

- [Przewodnik po platformie .NET Framework](../index.yml)
- [Co nowego](../whats-new/index.md)
- [Przeglądarka interfejsów API na platformie .NET](../../../api/index.md)
- [Przewodnik po rozwoju](../development-guide.md)
