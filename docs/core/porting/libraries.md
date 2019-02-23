---
title: Port bibliotek platformy .NET Core
description: Dowiedz się, jak przenieść projekty bibliotek z programu .NET Framework i .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 8709c4942bcd1b0fc7f0e75ee41e5c9a01df83ee
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745563"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port biblioteki .NET Framework i .NET Core

Dowiedz się, jak przenieść kod biblioteki .NET Framework i .NET Core, aby uruchomić dla wielu platform i Rozszerz zasięg aplikacji, które go używają.

## <a name="prerequisites"></a>Wymagania wstępne

W tym artykule założono, że możesz:

- Program Visual Studio 2017 r. lub nowszej.
  - .NET core nie jest obsługiwane we wcześniejszych wersjach programu Visual Studio
- Zrozumienie [zalecane przenoszenie procesu](index.md).
- Problem został rozwiązany w jakichkolwiek problemów z [zależności innych firm](third-party-deps.md).

Należy również zapoznać się z zawartością w następujących tematach:

[.NET standard](../../standard/net-standard.md)\
W tym temacie opisano formalną specyfikację interfejsów API platformy .NET, które mają być dostępne na wszystkich implementacji .NET.

[Pakiety, Metapakiety i struktury](~/docs/core/packages.md)   
W tym artykule omówiono sposób platformy .NET Core definiuje używa pakietów i sposobu pakietów informacje prasowe kod działający na wiele implementacji .NET.

[Tworzenie bibliotek za pomocą narzędzi międzyplatformowych](~/docs/core/tutorials/libraries.md)   
W tym temacie wyjaśniono, jak napisać biblioteki dla platformy .NET przy użyciu narzędzi interfejsu wiersza polecenia dla wielu platform.

[Dodatki do *csproj* formatu dla platformy .NET Core](~/docs/core/tools/csproj.md)   
W tym artykule opisano zmiany, które zostały dodane do pliku projektu w ramach przejścia *csproj* i MSBuild.

[Eksportowanie do programu .NET Core — analizowanie zależności innych firm](~/docs/core/porting/third-party-deps.md)   
W tym temacie omówiono przenośność zależności innych firm i co można zrobić podczas zależności pakietów NuGet nie zostanie uruchomiona na platformie .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Trwa przekierowywanie do .NET Framework 4.7.2 kodu .NET Framework

Jeśli Twój kod nie jest przeznaczony dla .NET Framework 4.7.2, zalecane jest przekierowanie do .NET Framework 4.7.2. Zapewnia to dostępność najnowszych alternatywy interfejsu API w sytuacjach, w którym .NET Standard nie obsługuje istniejących interfejsów API.

Dla każdego z projektów w programie Visual Studio, dla których chcesz port, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy projekt i wybierz pozycję **właściwości**.
1. W **platformę docelową** listy rozwijanej wybierz **.NET Framework 4.7.2**.
1. Ponowna kompilacja projektów.

Ponieważ teraz Twoje projekty ukierunkowane na .NET Framework 4.7.2, korzystać z tej wersji programu .NET Framework jako podstawa dla przenoszenie kodu.

## <a name="determining-the-portability-of-your-code"></a>Określanie przenośność kodu

Następnym krokiem jest, aby uruchomić analizator przenośności interfejsu API (ApiPort), aby wygenerować raport przenoszenia do analizy.

Upewnij się, że rozumiesz [analizator przenośności interfejsu API (ApiPort)](../../standard/analyzers/portability-analyzer.md) i jak można wygenerować raporty przenośność przeznaczonych dla platformy .NET Core. Jak to zrobić tym prawdopodobnie różni się w zależności od potrzeb i gustom osobistych. Poniżej przedstawiono kilka różnych metod. Może się okazać samodzielnie mieszanie kroki tych metod w zależności od struktury kodu.

### <a name="dealing-primarily-with-the-compiler"></a>Zajmowanie się przede wszystkim kompilator

Takie podejście może być najlepsze dla małych projektów lub projektów, które nie używają wielu interfejsów API programu .NET Framework. To podejście jest proste:

1. Opcjonalnie możesz uruchomić ApiPort nad projektem. Po uruchomieniu ApiPort, należy uzyskać wiedzę raportu na problemy, które będą potrzebne do adresu.
1. Skopiuj cały kod do nowego projektu platformy .NET Core.
1. Podczas odwoływania się do raportu przenośność (jeśli jest generowane), należy rozwiązać błędy kompilatora do momentu, w pełni kompiluje projekt.

Mimo że takie podejście jest bez struktury, skoncentrowane na kodzie podejście często prowadzi do szybkiego rozwiązywania problemów i może być najlepszym rozwiązaniem dla mniejszych projektów lub biblioteki. Projekt, który zawiera tylko modeli danych może być idealne kandydatem do tej metody.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Dokonywanie aktualizacji na .NET Framework, dopóki nie zostaną rozwiązane problemy

Takie podejście może być najlepiej, jeśli chcesz mieć kod, który kompiluje podczas całego procesu. To podejście jest następująca:

1. Uruchom ApiPort w projekcie.
1. Rozwiązywanie problemów z za pomocą różnych interfejsów API, które są zgodne.
1. Zwróć uwagę na obszary, gdzie masz możliwości używana zamiast bezpośredniego.
1. Powtórz wcześniejsze kroki dla wszystkich projektów, które jest przenoszenie, dopóki nie masz pewność, że każdy jest gotowa do skopiowania za pośrednictwem do nowego projektu platformy .NET Core.
1. Skopiuj kod do nowego projektu platformy .NET Core.
1. Pozwolimy na opracowanie wszelkie problemy, w którym zauważyć że zamiast bezpośredniego nie istnieje.

To podejście dokładnej jest bardziej ustrukturyzowane niż po prostu praca się błędy kompilatora, ale jest nadal stosunkowo skoncentrowane na kodzie i ma tę zaletę zawsze masz kod, który kompiluje. Sposób rozwiązania niektórych problemów, które nie może zostać zlikwidowane przez tylko przy użyciu innego interfejsu API może być różny. Może się okazać konieczne tworzenie bardziej kompleksowe planowanie dla niektórych projektów, które jest objęte dalej podejście.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Tworzenie kompleksowego planu ataku

Takie podejście może być najlepszym rozwiązaniem dla większych i bardziej złożonych projektów, gdzie całkowicie zdebugować niektóre obszary kodu lub restrukturyzacji kod może być konieczna Obsługa platformy .NET Core. To podejście jest następująca:

1. Uruchom ApiPort w projekcie.
1. Dowiedz się, gdzie każdy typ nieprzenośne służy i jak to ma wpływ na ogólną przenoszenia.
   - Zrozumienie natury tych typów. Są one niewielka liczba, ale używany często? Są one duże wiele, ale używanych rzadko? Ich użycie jest skoncentrowany, czy są rozmieszczone w całym kodzie?
   - Jest łatwy do izolowania kod, który nie jest przenośny, umożliwiając poradzenie sobie z tym bardziej efektywnie?
   - Czy musisz wykonać refaktoryzację kodu?
   - Dla tych typów, które nie są przenośne są alternatywne interfejsy API, które wykonania tego samego zadania? Na przykład jeśli używasz <xref:System.Net.WebClient> klasy, można używać <xref:System.Net.Http.HttpClient> klasy zamiast tego.
   - Istnieją różne przenośnych interfejsów API do wykonania zadania, nawet jeśli nie jest zamiennikiem? Na przykład jeśli używasz <xref:System.Xml.Schema.XmlSchema> można przeanalizować kodu XML, ale nie wymagają XML odnajdywania schematów, można użyć <xref:System.Xml.Linq> interfejsów API i implementowanie analizy samodzielnie zamiast polegania na interfejs API.
1. W przypadku zestawów, które są trudne do portu jest warte pozostawiania je w programie .NET Framework, teraz? Poniżej przedstawiono niektóre kwestie, należy wziąć pod uwagę:
   - Niektóre funkcje mogą mieć w bibliotece, która jest niezgodna z platformą .NET Core, ponieważ zbyt intensywnie korzysta się z funkcji .NET Framework lub specyficzne dla Windows. Jest warte pozostawiając tę funkcję teraz i zwalnianie wersji platformy .NET Core, biblioteki za pomocą funkcji tymczasowo do momentu zasoby są dostępne do portu funkcji?
   - Refaktoryzacja może pomóc?
1. Jest to uzasadnione do zapisania Twojej własnej implementacji niedostępny w .NET Framework API?
   Można rozważyć kopiowanie, modyfikowanie i wykorzystaniu kodu z [źródła programu .NET Framework odwołanie](https://github.com/Microsoft/referencesource). Odwołanie do kodu źródłowego jest licencjonowane w ramach [licencją MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), więc trzeba znaczące użytkownicy mogą korzystać ze źródłem jako podstawy własnego kodu. Pamiętaj tylko prawidłowo atrybutu firmy Microsoft w swoim kodzie.
1. Powtórz tę procedurę, zgodnie z potrzebami w różnych projektach.
 
Faza analizy może zająć trochę czasu, w zależności od rozmiaru bazy kodu. W perspektywie długoterminowej poświęcania czasu na tym etapie, aby dokładnie zrozumieć, w zakresie zmian i aby opracować plan zwykle oszczędza czas, szczególnie w przypadku złożonych bazy kodu.

Plan może obejmować wprowadzeniu istotnych zmian do Twojej bazy kodu podczas nadal przeznaczone dla .NET Framework 4.7.2, dzięki czemu to nieco bardziej ustrukturyzowane podejście poprzedniego. Jak obniżyć dotyczące wykonywania planu zależy od kodu.

### <a name="mixing-approaches"></a>Mieszanie metod

Istnieje prawdopodobieństwo, że będziesz mieszać powyższych podejść w poszczególnych projektów. Należy wykonać, co najodpowiedniejszy dla Ciebie i Twojej bazy kodu.

## <a name="porting-your-tests"></a>Przenoszenie testów

Najlepszym sposobem upewnij się, że wszystko działa, gdy zostały przeniesione kodu jest do testowania kodu, jak przenieść go do platformy .NET Core. Aby to zrobić, należy użyć struktura testowania, który kompiluje i uruchamia testy dla platformy .NET Core. Obecnie masz trzy opcje:

- [xUnit](https://xunit.github.io/)
  * [Wprowadzenie](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Narzędzie, aby przekonwertować Projekt narzędzia MSTest, xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Wprowadzenie](https://github.com/nunit/docs/wiki/Installation)
  * [Migrowanie z MSTest do NUnit wpis w blogu](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Zalecane podejście do przenoszenia

Ostatecznie przenoszenia nakład pracy zależy od intensywnie struktury kodu .NET Framework. Dobrym sposobem na porcie kodu jest przede wszystkim *podstawowy* biblioteki to podstawowe składniki kodu. Może to być modeli danych lub niektóre podstawowe klasy i metody, używanych przez wszystkie inne elementy bezpośrednio lub pośrednio.

1. Port projektu testowego, który testuje warstwy biblioteki, które są aktualnie przenoszenie.
1. Skopiuj podstawowy biblioteki do nowego projektu platformy .NET Core i wybierz wersję programu .NET Standard chcesz obsługiwać.
1. Wprowadź wszelkie zmiany, konieczne kod do skompilowania. Większość tego mogą wymagać Dodawanie zależności pakietów NuGet, aby Twoje *csproj* pliku.
1. Uruchom testy i wprowadzić wymagane poprawki.
1. Wybierz kolejna warstwa kodu do portu i powtórz wcześniejsze kroki.

Jeśli rozpoczynać podstawowej biblioteki i przenieść na zewnątrz od podstawy i testowania każdej warstwy, zgodnie z potrzebami przenoszenie jest systematyczne procesu, gdy problemy są izolowane do jednej warstwy kodu w czasie.

>[!div class="step-by-step"]
>[Next](project-structure.md)
