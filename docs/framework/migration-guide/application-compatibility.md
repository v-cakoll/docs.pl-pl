---
title: Zgodność aplikacji w programie .NET Framework
ms.date: 05/19/2017
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f547180995ec155f9121eeace109e7dfb07c7827
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790112"
---
# <a name="application-compatibility-in-the-net-framework"></a>Zgodność aplikacji w programie .NET Framework

## <a name="introduction"></a>Wprowadzenie
Zgodność to istotny cel każdej wersji platformy .NET. Zgodność gwarantuje, że każda wersja jest dodatkiem, dlatego poprzednie wersje nadal będą działały. Z drugiej strony zmiany poprzedniej funkcjonalności (w celu zwiększenia wydajności, rozwiązywania problemów z zabezpieczeniami lub rozwiązywania usterek) mogą spowodować problemy ze zgodnością w istniejącym kodzie lub istniejące aplikacje, które działają w nowszej wersji. .NET Framework rozpoznaje zmiany przekierowania i zmiany w czasie wykonywania. Zmiany dotyczące przekierowywania mają wpływ na aplikacje, które są przeznaczone dla określonej wersji .NET Framework ale działają w nowszej wersji. Zmiany w czasie wykonywania mają wpływ na wszystkie aplikacje działające w określonej wersji.

Każda aplikacja odwołuje się do określonej wersji .NET Framework, która może być określona przez:

- Definiowanie platformy docelowej w programie Visual Studio.
- Określanie platformy docelowej w pliku projektu.
- <xref:System.Runtime.Versioning.TargetFrameworkAttribute> Zastosowanie do kodu źródłowego.

Gdy program jest uruchamiany w nowszej wersji niż dostosowana, .NET Framework będzie używać zachowania quirked do naśladowania starszej wersji dostosowanej. Innymi słowy, aplikacja zostanie uruchomiona w nowszej wersji platformy, ale działa tak, jakby była uruchomiona w starszej wersji. Wiele problemów ze zgodnością między wersjami .NET Framework jest korygowanych przez ten model quirking. Wersja .NET Framework, do której odwołuje się aplikacja, jest określana przez docelową wersję zestawu wejścia dla domeny aplikacji, w której uruchomiono kod. Wszystkie dodatkowe zestawy ładowane w tym miejscu docelowym domeny aplikacji, które .NET Framework wersji. Na przykład w przypadku pliku wykonywalnego Struktura elementów wykonywalnych jest w trybie zgodności, w którym będą uruchamiane wszystkie zestawy w tej domenie aplikacji.

## <a name="runtime-changes"></a>Zmiany środowiska uruchomieniowego

Problemy dotyczące środowiska uruchomieniowego to te, które powstają, gdy nowe środowisko uruchomieniowe jest umieszczane na komputerze i są uruchamiane te same pliki binarne, ale jest widoczne inne zachowanie. Jeśli plik binarny został skompilowany dla .NET Framework 4,0, zostanie uruchomiony w trybie zgodności .NET Framework 4,0 w wersji 4,5 lub nowszej. Wiele zmian, które mają wpływ na 4,5, nie będzie miało wpływu na dane binarne skompilowane dla 4,0. Jest to specyficzne dla elementu AppDomain i zależy od ustawień zestawu wpisów.

## <a name="retargeting-changes"></a>Przekierowywanie zmian

Przekierowywanie problemów polega na tym, że w przypadku zestawu, który miał znaczenie 4,0, jest teraz ustawiona wartość Target 4,5. Teraz zestaw wprowadza do nowych funkcji, a także potencjalne problemy ze zgodnością dla starych funkcji. Jest to podyktowane przez zestaw wpisów, więc Aplikacja konsolowa, która używa zestawu lub witryny sieci Web, która odwołuje się do zestawu.

## <a name="net-compatibility-diagnostics"></a>Diagnostyka zgodności programu .NET

Diagnostyka zgodności programu .NET to Roslyn analizatory, które pomagają identyfikować problemy ze zgodnością aplikacji między wersjami .NET Framework. Ta lista zawiera wszystkie dostępne analizatory, chociaż tylko podzestaw zostanie zastosowany do każdej konkretnej migracji. Analizatory określiją, które problemy mają zastosowanie do planowanej migracji, i będą miały tylko te kwestie.

Każdy problem zawiera następujące informacje:

- Opis zmian w poprzedniej wersji.

- Wpływ zmiany na klientów i czy istnieją obejścia, aby zachować zgodność między wersjami.

- Ocena, jak ważna jest zmiana. Problem ze zgodnością aplikacji jest kategoryzowany w następujący sposób:

    |   |   |
    |---|---|
    |Duży|Znaczna zmiana wpływająca na dużą liczbę aplikacji lub wymagająca istotnej modyfikacji kodu.|
    |Mały|Zmiana wpływająca na niewielką liczbę aplikacji lub wymagająca drobnej modyfikacji kodu.|
    |Przypadek graniczny|Zmiana wpływająca na aplikacje w bardzo konkretnych, nietypowych scenariuszach.|
    |Przezroczyste|Zmiana bez zauważalnego wpływu na deweloperów lub użytkownika aplikacji.|

- Wersja wskazuje, kiedy po raz pierwszy pojawia się w strukturze. Niektóre zmiany są wprowadzane w określonej wersji i przywrócone w nowszej wersji. jest to również wskazane.

- Typ zmiany:

    |   |   |
    |---|---|
    |Przekierowanie|Zmiana ma wpływ na aplikacje, które są ponownie kompilowane pod kątem nowej wersji .NET Framework.|
    |Środowisko uruchomieniowe|Zmiana dotyczy istniejącej aplikacji, która jest przeznaczona dla poprzedniej wersji .NET Framework ale jest uruchamiana w nowszej wersji.|

- Narażone interfejsy API, jeśli istnieją.

- Identyfikatory dostępnej diagnostyki

## <a name="usage"></a>Użycie
Aby rozpocząć, wybierz typ zmiany zgodności poniżej:

- [Zmiany retargetingu](./retargeting/index.md)
- [Zmiany środowiska uruchomieniowego](./runtime/index.md)

## <a name="see-also"></a>Zobacz także

- [Wersje i zależności](versions-and-dependencies.md)
- [Co nowego](../whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../whats-new/whats-obsolete.md)
