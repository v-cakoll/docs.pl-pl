---
title: Biblioteki portów do programu .NET Core
description: Dowiedz się, jak przenieść projekty biblioteki z .NET Framework do .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 68fe36e543d949dc76bdb0c19ef3482936ad9e79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398910"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Port .NET Framework biblioteki do .NET Core

Dowiedz się, jak przenieść kod biblioteki .NET Framework do platformy .NET Core, gdzie działa na wielu platformach i rozszerza zasięg aplikacji, które go używają.

## <a name="prerequisites"></a>Wymagania wstępne

W tym artykule założono, że:

- Używasz programu Visual Studio 2017 lub nowszego. (.NET Core nie jest obsługiwana we wcześniejszych wersjach programu Visual Studio).
- Zrozumienie [zalecanego procesu przenoszenia](index.md).
- Rozwiązano wszelkie problemy z [zależnościami innych firm](third-party-deps.md).

Należy również zapoznać się z treścią następujących artykułów:

[Standard .NET](../../standard/net-standard.md)\
W tym artykule opisano formalną specyfikację interfejsów API .NET, które mają być dostępne we wszystkich implementacjach .NET.

[Pakiety, metapakiety i struktury](../packages.md)\
W tym artykule omówiono sposób, w jaki program .NET Core definiuje i używa pakietów oraz sposobu obsługi kodu obsługiwanego przez pakiety działające w wielu implementacjach programu .NET.

[Tworzenie bibliotek za pomocą narzędzi międzyplatformowych](../tutorials/libraries.md)\
W tym artykule wyjaśniono, jak pisać biblioteki przy użyciu .NET Core CLI.

[Dodatki do formatu *csproj* dla .NET Core](../tools/csproj.md)\
W tym artykule opisano zmiany, które zostały dodane do pliku projektu w ramach przenoszenia do *csproj* i MSBuild.

[Przenoszenie do .NET Core — analizowanie zależności innych firm](third-party-deps.md)\
W tym artykule omówiono przenośność zależności innych firm i co zrobić, gdy zależność pakietu NuGet nie jest uruchamiana na .NET Core.

## <a name="retarget-to-net-framework-472"></a>Ponowne kierowanie do .NET Framework 4.7.2

Jeśli kod nie jest przeznaczony dla .NET Framework 4.7.2, zaleca się ponowne kierowanie do .NET Framework 4.7.2. Zapewnia to dostępność najnowszych alternatyw interfejsu API w przypadkach, gdy standard .NET nie obsługuje istniejących interfejsów API.

Dla każdego z projektów, które chcesz port, wykonaj następujące czynności w programie Visual Studio:

1. Kliknij prawym przyciskiem myszy projekt i wybierz **polecenie Właściwości**.
1. W rozwijanej **platformie docelowej** wybierz pozycję **.NET Framework 4.7.2**.
1. Ponownie skompilować projekt.

Ponieważ projekty są teraz przeznaczone dla programu .NET Framework 4.7.2, użyj tej wersji programu .NET Framework jako bazy do przenoszenia kodu.

## <a name="determine-portability"></a>Określanie przenośności

Następnym krokiem jest uruchomienie analizatora przenośności interfejsu API (ApiPort) w celu wygenerowania raportu przenośności do analizy.

Upewnij się, że rozumiesz [analizator przenośności interfejsu API (ApiPort)](../../standard/analyzers/portability-analyzer.md) i jak wygenerować raporty przenośności dla kierowania .NET Core. Sposób, w jaki to zrobisz, różni się w zależności od potrzeb i osobistych upodobań. W poniższych sekcjach opisano kilka różnych podejść. Możesz znaleźć się mieszania kroki tych podejść w zależności od struktury kodu.

### <a name="deal-primarily-with-the-compiler"></a>Zajmij się przede wszystkim kompilatorem

Takie podejście działa dobrze w przypadku małych projektów lub projektów, które nie używają wielu interfejsów API platformy .NET Framework. Podejście jest proste:

1. Opcjonalnie uruchom ApiPort w projekcie. Jeśli uruchomisz ApiPort, zdobądź wiedzę z raportu na temat problemów, które musisz rozwiązać.
1. Skopiuj cały kod do nowego projektu .NET Core.
1. Podczas odwoływania się do raportu przenośności (jeśli generowane), rozwiązać błędy kompilatora, dopóki projekt w pełni kompiluje.

Mimo że jest nieustrukturyzowany, to podejście zorientowane na kod często szybko rozwiązuje problemy. Projekt, który zawiera tylko modele danych może być idealnym kandydatem do tego podejścia.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Pozostań w platformie .NET Framework do momentu rozwiązania problemów z przenośnością

Takie podejście może być najlepsze, jeśli wolisz mieć kod, który kompiluje się podczas całego procesu. Podejście jest następujące:

1. Uruchom ApiPort w projekcie.
1. Rozwiązaj problemy przy użyciu różnych interfejsów API, które są przenośne.
1. Zanotuj wszystkie obszary, w których nie możesz korzystać z bezpośredniej alternatywy.
1. Powtórz wcześniejsze kroki dla wszystkich projektów, które przenosisz, dopóki nie masz pewności, że każdy z nich jest gotowy do skopiowania do nowego projektu .NET Core.
1. Skopiuj kod do nowego projektu .NET Core.
1. Wypracować wszelkie problemy, w których zauważyłeś, że bezpośrednia alternatywa nie istnieje.

To ostrożne podejście jest bardziej ustrukturyzowane niż po prostu wypracowanie błędów kompilatora, ale nadal jest stosunkowo zorientowane na kod i ma tę zaletę, że zawsze ma kod, który kompiluje. Sposób rozwiązywania niektórych problemów, których nie można rozwiązać za pomocą innego interfejsu API, różni się znacznie. Może się okazać, że konieczne jest opracowanie bardziej kompleksowego planu dla niektórych projektów, który jest objęty następnym podejściem.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Opracowanie kompleksowego planu ataku

Takie podejście może być najlepsze dla większych i bardziej złożonych projektów, gdzie kod restrukturyzacji lub całkowicie przepisanie niektórych obszarów kodu może być konieczne do obsługi .NET Core. Podejście jest następujące:

1. Uruchom ApiPort w projekcie.
1. Dowiedz się, gdzie jest używany każdy typ nieprzenośny i jak to wpływa na ogólną przenośność.
   - Zrozumieć charakter tych typów. Czy są one małe, ale często używane? Czy są one duże w liczbie, ale rzadko używane? Czy ich stosowanie jest skoncentrowane, czy też rozprzestrzenia się w całym kodzie?
   - Czy łatwo jest wyizolować kod, który nie jest przenośny, dzięki czemu można sobie z nim poradzić bardziej efektywnie?
   - Czy musisz refaktoryzować kod?
   - Dla tych typów, które nie są przenośne, czy istnieją alternatywne interfejsy API, które realizują to samo zadanie? Na przykład jeśli używasz <xref:System.Net.WebClient> klasy, może być w stanie <xref:System.Net.Http.HttpClient> użyć klasy zamiast tego.
   - Czy istnieją różne przenośne interfejsy API dostępne do wykonania zadania, nawet jeśli nie jest to zamiennik drop-in? Na przykład jeśli używasz <xref:System.Xml.Schema.XmlSchema> do analizy XML, ale nie wymagają odnajdowania <xref:System.Xml.Linq> schematu XML, można użyć interfejsów API i zaimplementować analizowanie siebie, w przeciwieństwie do polegania na interfejsie API.
1. Jeśli masz zestawy, które są trudne do portu, warto zostawić je na .NET Framework na razie? Oto kilka rzeczy do rozważenia:
   - Niektóre funkcje w bibliotece mogą być niezgodne z programem .NET Core, ponieważ zbyt mocno zależy ona od platformy .NET Framework lub funkcji specyficznych dla systemu Windows. Czy warto zostawić tę funkcję za sobą na razie i zwolnić tymczasową wersję .NET Core biblioteki z mniejszą funkcjonalnością, dopóki zasoby nie będą dostępne do przeniesienia funkcji?
   - Czy refaktoryzacja pomoże?
1. Czy uzasadnione jest napisanie własnej implementacji niedostępnego interfejsu API .NET Framework?
   Można rozważyć kopiowanie, modyfikowanie i używanie kodu ze [źródła referencyjnego .NET Framework](https://github.com/Microsoft/referencesource). Referencyjny kod źródłowy jest licencjonowany na licencji [MIT,](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)więc masz znaczną swobodę korzystania ze źródła jako podstawy własnego kodu. Pamiętaj tylko, aby prawidłowo przypisać microsoft w kodzie.
1. Powtórz ten proces zgodnie z potrzebami dla różnych projektów.

Faza analizy może zająć trochę czasu w zależności od rozmiaru bazy kodu. Spędzanie czasu w tej fazie, aby dokładnie zrozumieć zakres potrzebnych zmian i opracować plan zwykle oszczędza czas w dłuższej perspektywie, szczególnie jeśli masz złożoną bazę kodu.

Plan może obejmować wprowadzenie istotnych zmian w bazie kodu, a jednocześnie kierowania .NET Framework 4.7.2, dzięki czemu jest to bardziej ustrukturyzowana wersja poprzedniego podejścia. Sposób wykonywania planu zależy od bazy kodu.

### <a name="mixed-approach"></a>Podejście mieszane

Jest prawdopodobne, że będziesz mieszać powyższe podejścia na podstawie podlany projektu. Należy zrobić to, co ma największy sens dla Ciebie i dla swojej bazy kodu.

## <a name="port-your-tests"></a>Przenieś swoje testy

Najlepszym sposobem, aby upewnić się, że wszystko działa po przesunieniu kodu jest przetestowanie kodu podczas przenoszenia go do .NET Core. Aby to zrobić, należy użyć struktury testowania, która tworzy i uruchamia testy dla .NET Core. Obecnie dostępne są trzy opcje:

- [Xunit](https://xunit.github.io/)
  - [Wprowadzenie](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Narzędzie do konwertowania projektu MSTest na xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [Nunit](https://nunit.org/)
  - [Wprowadzenie](https://github.com/nunit/docs/wiki/Installation)
  - [Wpis w blogu o migracji z mstestu do jednostki NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Zalecane podejście

Ostatecznie nakład usiłuje w dużym stopniu od struktury kodu programu .NET Framework. Dobrym sposobem przeniesienia kodu jest rozpoczęcie od *podstawy* biblioteki, która jest podstawowymi składnikami kodu. Może to być modele danych lub inne podstawowe klasy i metody, które wszystko inne używa bezpośrednio lub pośrednio.

1. Przenieś projekt testowy, który testuje warstwę biblioteki, która jest aktualnie przewiona.
1. Skopiuj przez podstawę biblioteki do nowego projektu .NET Core i wybierz wersję standardu .NET, który chcesz obsługiwać.
1. Wyczyść wszelkie zmiany potrzebne do uzyskania kodu do skompilowania. Wiele z tego może wymagać dodania zależności pakietów NuGet do pliku *csproj.*
1. Uruchom testy i wprowadź niezbędne zmiany.
1. Wybierz następną warstwę kodu do portu i powtórz wcześniejsze kroki.

Jeśli zaczniesz od podstawy biblioteki i przenieść się na zewnątrz od podstawy i przetestować każdą warstwę w razie potrzeby, przenoszenie jest procesem systematycznym, w którym problemy są izolowane do jednej warstwy kodu naraz.

## <a name="next-steps"></a>Następne kroki

>[!div class="nextstepaction"]
>[Organizowanie projektów dla platformy .NET Core](project-structure.md)
