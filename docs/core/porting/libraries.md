---
title: Biblioteki portów do programu .NET Core
description: Dowiedz się, jak przenieść projekty biblioteki z .NET Framework do programu .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 3e3c613f6be50ae5ff2b07052c7c1bced2047855
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105289"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Porty .NET Framework biblioteki do programu .NET Core

Dowiedz się, jak przenieść kod biblioteki .NET Framework do programu .NET Core, aby uruchamiać Międzyplatformowe i rozszerzać zasięg aplikacji, które go używają.

## <a name="prerequisites"></a>Wymagania wstępne

W tym artykule przyjęto założenie, że:

- Używa programu Visual Studio 2017 lub nowszego.
  - Platforma .NET Core nie jest obsługiwana we wcześniejszych wersjach programu Visual Studio
- Zapoznaj się z [zalecanym procesem przenoszenia](index.md).
- Rozwiązano wszelkie problemy związane [](third-party-deps.md)z zależnościami innych firm.

Należy również zapoznać się z treścią następujących tematów:

[.NET Standard](../../standard/net-standard.md)\
W tym temacie opisano formalne specyfikacje interfejsów API platformy .NET, które mają być dostępne we wszystkich implementacjach platformy .NET.

[Pakiety, aplikacje i struktury](../packages.md)   
W tym artykule omówiono sposób definiowania i używania pakietów przez platformę .NET Core oraz sposób obsługi kodu działającego w wielu implementacjach platformy .NET.

[Tworzenie bibliotek przy użyciu narzędzi międzyplatformowych](../tutorials/libraries.md)   
W tym temacie wyjaśniono, jak pisać biblioteki dla platformy .NET przy użyciu międzyplatformowych narzędzi interfejsu wiersza polecenia.

[Dodatki do formatu *csproj* dla platformy .NET Core](../tools/csproj.md)   
W tym artykule opisano zmiany, które zostały dodane do pliku projektu w ramach przenoszenia do *csproj* i MSBuild.

[Przenoszenie do platformy .NET Core — analizowanie zależności innych firm](third-party-deps.md)   
W tym temacie omówiono przenośność zależności innych firm i czynności, które należy wykonać, gdy zależność pakietu NuGet nie jest uruchamiana na platformie .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Przekieruj kod .NET Framework do .NET Framework 4.7.2

Jeśli Twój kod nie jest celem .NET Framework 4.7.2, zalecamy przekierowanie do .NET Framework 4.7.2. Zapewnia to dostępność najnowszych alternatywnych rozwiązań API dla przypadków, w których .NET Standard nie obsługuje istniejących interfejsów API.

Dla każdego projektu w programie Visual Studio należy wykonać następujące czynności:

1. Kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Właściwości**.
1. Na liście rozwijanej **platforma** docelowa wybierz pozycję **.NET Framework 4.7.2**.
1. Ponowne Kompilowanie projektów.

Ponieważ projekty są teraz docelowe .NET Framework 4.7.2, Użyj tej wersji .NET Framework jako podstawy do przenoszenia kodu.

## <a name="determining-the-portability-of-your-code"></a>Określanie przenośności kodu

Następnym krokiem jest uruchomienie analizatora przenośności interfejsu API (ApiPort) w celu wygenerowania raportu przenośności na potrzeby analizy.

Upewnij się, że rozumiesz [analizatora przenośności interfejsu API (ApiPort)](../../standard/analyzers/portability-analyzer.md) i jak generować raporty dotyczące przenośności dla platformy .NET Core. Jak to możliwe, może się to różnić w zależności od potrzeb i zasmaków osobistych. Poniżej przedstawiono kilka różnych metod. W zależności od tego, jak kod jest strukturalny, możesz się doejść do mieszania kroków tych metod.

### <a name="dealing-primarily-with-the-compiler"></a>Postępowanie głównie z kompilatorem

Takie podejście może być najlepszym rozwiązaniem dla małych projektów lub projektów, które nie używają wielu .NET Framework interfejsów API. Podejście jest proste:

1. Opcjonalnie Uruchom ApiPort w projekcie. W przypadku uruchomienia ApiPort należy uzyskać informacje z raportu dotyczące problemów, które trzeba rozwiązać.
1. Kopiuj cały kod do nowego projektu .NET Core.
1. W odniesieniu do raportu przenośności (jeśli został wygenerowany) Rozwiązuj błędy kompilatora do momentu całkowitego skompilowania projektu.

Chociaż takie podejście jest pozbawione struktury, podejście ukierunkowane na kod często prowadzi do szybkiego rozwiązywania problemów i może być najlepszym rozwiązaniem dla mniejszych projektów lub bibliotek. Projekt, który zawiera tylko modele danych, może być idealnym kandydatem do tego podejścia.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>W .NET Framework do momentu rozwiązania problemów z przenośnością

Takie podejście może być najlepszym rozwiązaniem, jeśli wolisz mieć kod, który kompiluje się podczas całego procesu. Podejście jest następujące:

1. Uruchom ApiPort w projekcie.
1. Rozwiązywanie problemów przy użyciu różnych interfejsów API, które są przenośne.
1. Zanotuj wszystkie obszary, w których nie można użyć bezpośredniej alternatywy.
1. Powtórz poprzednie kroki dla wszystkich projektów, które są używane, dopóki nie masz pewności, że wszystkie są gotowe do skopiowania do nowego projektu .NET Core.
1. Skopiuj kod do nowego projektu .NET Core.
1. Wykorzystaj wszelkie problemy, w których zauważono, że bezpośrednia alternatywa nie istnieje.

To staranne podejście jest bardziej strukturalne niż zwykłe wykonywanie błędów kompilatora, ale nadal jest relatywnie ukierunkowane na kod i ma korzyść, która kompiluje kod. Sposób rozwiązywania niektórych problemów, których nie można rozwiązać przy użyciu innego interfejsu API, różni się znacznie. Może się okazać, że konieczne jest opracowanie bardziej kompleksowego planu dla niektórych projektów, który jest objęty kolejnym podejściem.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Opracowywanie kompleksowego planu ataków

Takie podejście może być najlepszym rozwiązaniem w przypadku większych i bardziej złożonych projektów, w przypadku których kod restrukturyzacji lub całkowite ponowne zapisanie niektórych obszarów kodu mogą być niezbędne do obsługi platformy .NET Core. Podejście jest następujące:

1. Uruchom ApiPort w projekcie.
1. Informacje o tym, gdzie jest używany każdy typ nieprzenośny i jak ma to wpływ na ogólną przenośność.
   - Zrozumienie charakteru tych typów. Czy są one małe w liczbie, ale używane często? Czy są one duże w liczbie, ale używane rzadko? Czy ich użycie jest skoncentrowane lub czy jest rozłożone w całym kodzie?
   - Czy łatwo jest izolować kod, który nie jest przenośny, aby można było go bardziej efektywnie rozwiązać?
   - Czy musisz ponownie wykonać swój kod?
   - Czy dla tych typów, które nie są przenośne, są alternatywne interfejsy API, które spełniają to samo zadanie? Na przykład jeśli korzystasz z <xref:System.Net.WebClient> klasy, możesz zamiast tego <xref:System.Net.Http.HttpClient> użyć klasy.
   - Czy istnieją różne przenośne interfejsy API dostępne do wykonania zadania, nawet jeśli nie jest to zamiennik? Na przykład jeśli <xref:System.Xml.Schema.XmlSchema> używasz programu do analizowania kodu XML, ale nie wymagasz odnajdywania schematu XML, <xref:System.Xml.Linq> możesz używać interfejsów API i implementować analizę, zamiast korzystać z interfejsu API.
1. Jeśli masz zestawy, które są trudne do portów, czy warto teraz pozostawić je na .NET Framework? Oto kilka kwestii, które należy wziąć pod uwagę:
   - W bibliotece mogą działać pewne funkcje, które są niezgodne z platformą .NET Core, ponieważ opierają się one zbyt mocno na .NET Framework lub funkcjach specyficznych dla systemu Windows. Czy ta funkcja jest powarta w tym momencie, i tymczasowo zwalniasz wersję biblioteki platformy .NET Core z mniejszą funkcjonalnością do momentu dostępności zasobów do przenoszenia funkcji?
   - Czy chcesz uzyskać pomoc dotyczącą refaktoryzacji?
1. Czy warto napisać własną implementację niedostępnego interfejsu API .NET Framework?
   Można rozważyć możliwość kopiowania, modyfikowania i używania kodu ze [źródła odwołania .NET Framework](https://github.com/Microsoft/referencesource). Kod źródłowy odwołania jest licencjonowany w ramach [licencji MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), więc masz znaczną swobodę używania źródła jako podstawy dla własnego kodu. Upewnij się, że poprawnie pokoduje firmę Microsoft w kodzie.
1. Powtórz ten proces zgodnie z wymaganiami dla różnych projektów.
 
Faza analizy może zająć trochę czasu w zależności od rozmiaru bazy kodu. Czas wydatków w tej fazie w celu dokładnego zrozumienia zakresu zmian, które są potrzebne, i opracowania planu zwykle oszczędza czas w długim przebiegu, szczególnie jeśli masz złożoną bazę kodu.

Twój plan może polegać na wprowadzeniu znaczących zmian w bazie kodu, gdy nadal są dostępne .NET Framework 4.7.2, co sprawia, że jest to bardziej strukturalna wersja poprzedniego podejścia. Informacje o wykonywaniu planu są zależne od bazy kodu.

### <a name="mixing-approaches"></a>Mieszanie metod

Istnieje duże podejście do powyższego podejścia dla poszczególnych projektów. Należy to zrobić najlepiej dla Ciebie i dla bazy kodu.

## <a name="porting-your-tests"></a>Przenoszenie testów

Najlepszym sposobem, aby upewnić się, że wszystko działa, gdy Port został przetestowany w celu przetestowania kodu podczas jego portów do .NET Core. W tym celu należy użyć platformy testowania, która kompiluje i uruchamia testy dla platformy .NET Core. Obecnie są dostępne trzy opcje:

- [xUnit](https://xunit.github.io/)
  - [Wprowadzenie](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Narzędzie do konwersji projektu MSTest na xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Wprowadzenie](https://github.com/nunit/docs/wiki/Installation)
  - [Wpis w blogu dotyczący migracji z MSTest do NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Zalecane podejście do przenoszenia

W rezultacie nakłady pracy związane z przenoszeniem są zależne od tego, jak kod .NET Framework ma strukturę. Dobrym sposobem na port kodu jest rozpoczęcie od *podstaw* biblioteki, które są podstawowymi składnikami kodu. Mogą to być modele danych lub inne klasy podstawowe i metody, które pozostałe używają bezpośrednio lub pośrednio.

1. Port projektu testowego, który testuje warstwę biblioteki aktualnie przeznaczoną do przenoszenia.
1. Skopiuj bazę biblioteki do nowego projektu .NET Core i wybierz wersję .NET Standard, która ma być obsługiwana.
1. Wprowadź wszelkie zmiany potrzebne do uzyskania kodu do skompilowania. Większość może wymagać dodania zależności pakietów NuGet do pliku *csproj* .
1. Uruchom testy i wprowadź wszelkie potrzebne zmiany.
1. Wybierz następną warstwę kodu do przełączenia, a następnie powtórz poprzednie kroki.

Jeśli zaczynasz od podstawowej biblioteki i przeniesiesz ją na zewnątrz i przetestujesz każdą warstwę w razie potrzeby, port jest procesem systematycznym, w którym problemy są izolowane od jednej warstwy kodu naraz.

>[!div class="step-by-step"]
>[Next](project-structure.md)
