---
title: "Zgodność aplikacji w programie .NET Framework"
ms.custom: 
ms.date: 05/19/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
- app-compat
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
caps.latest.revision: "19"
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e67fff19c4b187010b35519081f46e11effbad6c
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="application-compatibility-in-the-net-framework"></a>Zgodność aplikacji w programie .NET Framework

## <a name="introduction"></a>Wprowadzenie
Zgodność jest bardzo ważne celem każdej wersji platformy .NET. Zgodności zapewni, że każda wersja dodatku, więc poprzedniej wersji będą nadal działać. Z drugiej strony zmiany w funkcjonalności poprzedniego (w celu zwiększenia wydajności i rozwiązać problemy zabezpieczeń, lub błędów) może spowodować problemy ze zgodnością w istniejący kod lub istniejące aplikacje uruchamiane w nowszej wersji. .NET Framework rozpoznaje zmiany retargetingu i środowiska wykonawczego. Zmiany retargetingu wpływ na aplikacje docelowe określonej wersji programu .NET Framework, ale są uruchomione w nowszej wersji. Zmiany środowiska uruchomieniowego wpływają na wszystkie aplikacje uruchomione na określonej wersji.

Każda aplikacja jest przeznaczony dla określonej wersji programu .NET Framework, który może zostać określony przez:

* Definiowanie platformy docelowej w programie Visual Studio.
* Określenie platformę docelową w pliku projektu.
* Stosowanie <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.

Uruchomionej na nowszą wersję niż co był przeznaczony quirked zachowanie programu .NET Framework będą używane do naśladować starszą wersję docelową. Innymi słowy aplikacja będzie uruchomić na nowszą wersję Framework, ale działa tak, jakby działa w starszej wersji. Wiele problemów ze zgodnością między wersjami programu .NET Framework, zostały skorygowane przez ten model quirking.

## <a name="runtime-changes"></a>Zmiany środowiska uruchomieniowego

Problemy dotyczące środowiska uruchomieniowego to wystąpić, gdy nowe środowisko uruchomieniowe znajduje się na komputerze i są uruchamiane w tej samej plików binarnych, ale pojawia się inaczej. Jeśli dane binarne został skompilowany dla platformy .NET Framework 4.0, zostanie uruchomiony w trybie zgodności programu .NET Framework 4.0, 4.5 lub nowszej wersji. Wiele zmian, które mają wpływ na 4.5 nie dotyczy pliku binarnego skompilowana dla wersji 4.0. To jest specyficzne dla domeny aplikacji i zależy od ustawień zestawu wpisu.

## <a name="retargeting-changes"></a>Zmiany retargetingu

Problemy przekierowania to wystąpić, gdy zestaw, który był celem 4.0 jest teraz skonfigurowana do docelowego 4.5. Zestaw zdecyduje się teraz do nowych funkcji, a także potencjalnych problemów ze zgodnością ze starego funkcji. Ponownie, to jest zależna zestawu wpisu, więc aplikacji konsoli, która używa zestawu lub witryny sieci Web, który odwołuje się do zestawu.

## <a name="net-compatibility-diagnostics"></a>Diagnostyka zgodności platformy .NET

Diagnostyka zgodności .NET są zasilane Roslyn analizatorów, które pomagają zidentyfikować problemy ze zgodnością aplikacji między wersjami programu .NET Framework. Ta lista zawiera wszystkie analizatory dostępne, mimo że tylko podzestaw będą stosowane do dowolnego migracji. Analizatory określają problemy, które mają zastosowanie w przypadku planowanej migracji i tylko powierzchni te.

Każde wydanie obejmuje następujące informacje:

-   Opis zmiany z poprzedniej wersji.

-   Jak zmiana wpływa na klientów oraz czy wszystkie obejścia są dostępne w celu zachowania zgodności między wersjami.

-   Ocena jak ważna jest zmiana. Problem ze zgodnością aplikacji są podzielone na następujące kategorie:

    |   |   |
    |---|---|
    |Główne|Znaczące zmiany, która ma wpływ na wiele aplikacji lub wymaga znacznej modyfikacji kodu.|
    |Pomocnicza|Zmiana, który wpływa na małej liczby aplikacji lub wymagają drobne zmiany kodu.|
    |Przypadek krawędzi|Zmiana wpływa na aplikacje w scenariuszach bardzo określone, rzadko.|
    |Przezroczyste|Zmiana nie wpływa na deweloperem aplikacji lub użytkownika.|

-   Wersja wskazuje, kiedy zmiany najpierw zostanie wyświetlony w ramach. Niektóre zmiany są wprowadzane w przypadku konkretnej wersji i przywrócone w nowszej wersji; który wskazane jest także.

-   Typ zmiany:

    |   |   |
    |---|---|
    |Przekierowania|Zmiana wpływa na aplikacje, które są ponownie skompilowana do nowej wersji programu .NET Framework.|
    |Środowisko uruchomieniowe|Zmiana wpływa na istniejących aplikacji, która jest przeznaczony dla poprzedniej wersji programu .NET Framework, ale działa w nowszej wersji.|

-   Dotyczy interfejsy API, jeśli istnieje.

-   Identyfikatory dostępne diagnostyki

## <a name="usage"></a>Użycie
Aby rozpocząć, wybierz typ zmiany zgodności poniżej:

* [Zmiany retargetingu](./retargeting/index.md)
* [Zmiany środowiska uruchomieniowego](./runtime/index.md)


## <a name="see-also"></a>Zobacz też

* [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
* [Nowości](../../../docs/framework/whats-new/index.md)
* [Co to jest przestarzałe w bibliotece klas](../../../docs/framework/whats-new/whats-obsolete.md)
