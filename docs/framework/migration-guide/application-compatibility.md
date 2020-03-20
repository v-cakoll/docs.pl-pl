---
title: Zmiany w czasie wykonywania i retargetingu — .NET Framework
ms.date: 10/29/2019
helpviewer_keywords:
- application compatibility
- .NET Framework application compatibility
- .NET Framework changes
ms.assetid: c4ba3ff2-fe59-4c5d-9e0b-86bba3cd865c
ms.openlocfilehash: c46f781d495b87a4f24e77935df7c4814c8567ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73196699"
---
# <a name="application-compatibility-in-the-net-framework"></a>Zgodność aplikacji w ramach .NET Framework

Zgodność jest ważnym celem każdej wersji .NET. Zgodność zapewnia, że każda wersja jest dodatek, więc poprzednie wersje będą nadal działać. Z drugiej strony zmiany w poprzedniej funkcjonalności (na przykład w celu zwiększenia wydajności, rozwiązania problemów z zabezpieczeniami lub naprawienia błędów) mogą powodować problemy ze zgodnością w istniejącym kodzie lub istniejących aplikacjach uruchamianych w nowszej wersji.

Każda aplikacja jest przeznaczona dla określonej wersji programu .NET Framework według:

- Definiowanie struktury docelowej w programie Visual Studio.
- Określanie struktury docelowej w pliku projektu.
- Stosowanie a <xref:System.Runtime.Versioning.TargetFrameworkAttribute> do kodu źródłowego.

Podczas migracji z jednej wersji programu .NET Framework do innej istnieją dwa typy zmian, które należy wziąć pod uwagę:

- [Zmiany w czasie wykonywania](#runtime-changes)
- [Zmiana celu](#retargeting-changes)

## <a name="runtime-changes"></a>Zmiany środowiska uruchomieniowego

Problemy ze środowiska wykonawczego są te, które pojawiają się, gdy nowy środowisko uruchomieniowe jest umieszczany na komputerze i zmiany zachowania aplikacji. Podczas uruchamiania w nowszej wersji niż to, co było ukierunkowane, .NET Framework używa *dziwaczne* zachowanie naśladować starszą wersję docelową. Aplikacja działa w nowszej wersji, ale działa tak, jakby była uruchomiona w starszej wersji. Wiele problemów ze zgodnością między wersjami programu .NET Framework są złagodzone za pośrednictwem tego modelu dziwactwa. Na przykład jeśli plik binarny został skompilowany dla programu .NET Framework 4.0, ale działa na komputerze z programem .NET Framework 4.5 lub nowszym, działa w trybie zgodności programu .NET Framework 4.0. Oznacza to, że wiele zmian w nowszej wersji nie wpływa na binarne.

Wersja programu .NET Framework, która jest przeznaczona dla aplikacji, jest określana przez docelową wersję zestawu wpisu dla domeny aplikacji, w których uruchamia się kod. Wszystkie dodatkowe zestawy załadowane w tej domenie aplikacji docelowej tej wersji. Na przykład w przypadku pliku wykonywalnego wersja, w którą obiekty docelowe wykonywalne jest trybem zgodności, w których działają wszystkie zestawy w tej domenie aplikacji.

Aby wyświetlić listę zmian w środowisku uruchomieniowym, które mają zastosowanie do twojego środowiska, wybierz aktualnie kierowaną wersję programu .NET Framework, a następnie wersję, do której chcesz przeprowadzić migrację:

[!INCLUDE[versionselector](../../../includes/migration-guide/runtime/versionselector.md)]

## <a name="retargeting-changes"></a>Zmiany retargetingu

Zmiany retargetingu są te, które powstają, gdy zestaw jest ponownie skompilowany do docelowej nowszej wersji. Kierowanie na nowszą wersję oznacza, że zestaw wybiera nowe funkcje, a także potencjalne problemy ze zgodnością starych funkcji.

Aby wyświetlić listę zmian retargetingu, które mają zastosowanie do twojego środowiska, wybierz wersję programu .NET Framework, na którą aktualnie kierujesz reklamy, a następnie wersję, do której chcesz przeprowadzić migrację:

[!INCLUDE[versionselector](../../../includes/migration-guide/retargeting/versionselector.md)]

## <a name="impact-classification"></a>Klasyfikacja wpływu

W tematach opisujących zmiany środowiska uruchomieniowego i retargetingu, na przykład [zmiany retargetingu w celu migracji z 4.7.2 do 4.8,](retargeting/4.7.2-4.8.md)poszczególne elementy są klasyfikowane według ich oczekiwanego wpływu w następujący sposób:

**Głównych**\
Istotna zmiana, która wpływa na dużą liczbę aplikacji lub która wymaga znacznej modyfikacji kodu.

**Drobne**\
Zmiana, która wpływa na niewielką liczbę aplikacji lub która wymaga niewielkiej modyfikacji kodu.

**Obudowa krawędzi**\
Zmiana, która wpływa na aplikacje w bardzo konkretnych scenariuszach, które nie są powszechne.

**Przezroczyste**\
Zmiana, która nie ma zauważalnego wpływu na dewelopera lub użytkownika aplikacji. Aplikacja nie powinna wymagać modyfikacji z powodu tej zmiany.

## <a name="see-also"></a>Zobacz też

- [Wersje i zależności](versions-and-dependencies.md)
- [Co nowego](../whats-new/index.md)
- [Co jest przestarzałe](../whats-new/whats-obsolete.md)
