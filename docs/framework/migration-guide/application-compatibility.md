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
ms.openlocfilehash: 1939666b3dd271959c418e3d714b177e170fcd04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595984"
---
# <a name="application-compatibility-in-the-net-framework"></a>Zgodność aplikacji w programie .NET Framework

## <a name="introduction"></a>Wprowadzenie
Zgodność jest bardzo ważne celem każdej wersji platformy .NET. Zgodność zapewnia każdej wersji dodatku, więc poprzedniej wersji będą nadal działać. Z drugiej strony zmiany w funkcjonalności poprzedniego (w celu zwiększenia wydajności i rozwiązywać problemy z bezpieczeństwem, lub naprawić usterki) może spowodować problemy ze zgodnością w istniejącym kodzie lub istniejące aplikacje uruchamiane w nowszej wersji. .NET Framework rozpoznaje przekierowanie zmiany i zmiany środowiska uruchomieniowego. Przekierowanie zmiany wpływają na aplikacje, które odwoływać się do określonej wersji programu .NET Framework, ale działają w nowszej wersji. Zmiany środowiska uruchomieniowego wpływają na wszystkie aplikacje uruchomione na określonej wersji.

Każda aplikacja jest przeznaczony dla określonej wersji programu .NET Framework, który może zostać określony przez:

* Definiowanie platformy docelowej w programie Visual Studio.
* Określanie platformy docelowej w pliku projektu.
* Stosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.

Podczas uruchamiania na nowszą wersję niż co został określony, .NET Framework użyje quirked zachowanie do naśladowania starszej wersji docelowej. Innymi słowy aplikacja są uruchamiane w nowszej wersji Framework ale działać tak, jakby działa starsza wersja. Wiele problemów ze zgodnością między wersjami programu .NET Framework zostały skorygowane przez ten model quirking. Wersja programu .NET Framework określone przez wersję docelową zestawu wpis dla domeny aplikacji, której kod jest uruchomiony w odpowiedniej aplikacji. Wszystkie dodatkowe zestawy ładowane w przeznaczonych domeny aplikacji tej wersji programu .NET Framework. Na przykład w przypadku pliku wykonywalnego programu framework cele pliku wykonywalnego jest tryb zgodności wszystkich zestawów, w tym elemencie AppDomain zostanie uruchomiony w obszarze.

## <a name="runtime-changes"></a>Zmiany środowiska uruchomieniowego

Problemy w czasie wykonywania są te, które powstają, gdy nowe środowisko uruchomieniowe znajduje się na komputerze są uruchamiane w tych samych plików binarnych, ale inne zachowanie jest widoczny. Jeśli plik binarny został skompilowany dla programu .NET Framework 4.0, będzie ona uruchamiana w trybie zgodności programu .NET Framework 4.0 w wersji 4.5 lub nowszej. Nie wpływa wiele zmian, które wpływają na 4.5 plik binarny skompilowane dla wersji 4.0. To jest specyficzne dla domeny aplikacji i zależy od ustawień zestawu wpisu.

## <a name="retargeting-changes"></a>Zmiany retargetingu

Przekierowanie problemy są tymi, które powstają, gdy zestaw, który był celem 4.0 jest równa docelowej 4.5. Teraz zestawu zdecyduje się na nowe funkcje, a także potencjalnych problemów ze zgodnością do starej funkcji. Ponownie, to jest zależna od zestawu wpisu, więc aplikacja konsoli, która używa zestawu lub witryny sieci Web, która odwołuje się do zestawu.

## <a name="net-compatibility-diagnostics"></a>Diagnostyka zgodności platformy .NET

Diagnostyka zgodności platformy .NET są analizatory bazujących na programie Roslyn, które pomagają identyfikować problemy ze zgodnością aplikacji między wersjami programu .NET Framework. Ta lista zawiera wszystkie dostępne, analizatorów, mimo że tylko ich podzestaw będą stosowane do dowolnej dotyczące migracji. Analizatory określi się problemy, które są odpowiednie dla planowanej migracji i ujawni tylko te.

Każde wydanie obejmuje następujące informacje:

-   Opis co zmieniło się od poprzedniej wersji.

-   Wpływ zmiany na klientów i tego, czy wszystkie rozwiązania są dostępne w celu zachowania zgodności między wersjami.

-   Ocena jak ważne jest zmiana. Problem ze zgodnością aplikacji są podzielone na następujące kategorie:

    |   |   |
    |---|---|
    |Duży|Istotną zmianę, którą ma wpływ na dużej liczby aplikacji lub wymaga znacznej modyfikacji kodu.|
    |Mały|Zmiana, to ma wpływ na niewielką liczbę aplikacji lub wymagają drobnych modyfikacji kodu.|
    |Przypadek krawędzi|Zmiana, który wpływa na aplikacje bardzo specyficzny, nietypowych scenariuszy.|
    |Przezroczyste|Zmiana nie wpływa na dewelopera aplikacji lub użytkownika.|

-   Wersja wskazuje, kiedy zmiany po raz pierwszy występuje w ramach. Niektóre ze zmian wprowadzonych w określonej wersji i przywrócić w nowszej wersji; wskazane jest także.

-   Typ zmiany:

    |   |   |
    |---|---|
    |Przekierowanie|Zmiana wpływa na aplikacje, które są ponownie kompilowane pod kątem nowych wersji programu .NET Framework.|
    |Środowisko uruchomieniowe|Zmiana wpływa na istniejącej aplikacji, który jest przeznaczony dla poprzednich wersji programu .NET Framework, ale działa w nowszej wersji.|

-   Dotyczy interfejsów API, jeśli istnieje.

-   Identyfikatory dostępne diagnostyki

## <a name="usage"></a>Użycie
Aby rozpocząć, wybierz typ zmiany zgodności poniżej:

* [Zmiany retargetingu](./retargeting/index.md)
* [Zmiany środowiska uruchomieniowego](./runtime/index.md)


## <a name="see-also"></a>Zobacz także

- [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
- [Co nowego](../../../docs/framework/whats-new/index.md)
- [Przestarzałe elementy w ułatwieniach dostępu](../../../docs/framework/whats-new/whats-obsolete.md)
