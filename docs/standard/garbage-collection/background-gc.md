---
title: Odzyskiwanie pamięci w tle
description: Informacje o wyrzucaniu elementów bezużytecznych w programie .NET i sposobie ich użycia w wyrzucaniu elementów bezużytecznych w stacji roboczej
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: 780503288d3474cd99a595bdbd52c3a5abba5308
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990230"
---
# <a name="background-garbage-collection"></a>Odzyskiwanie pamięci w tle

W wyrzucaniu elementów bezużytecznych w tle (GC), generacji tymczasowe (0 i 1) są zbierane zgodnie z wymaganiami, gdy trwa zbieranie danych generacji 2. Wyrzucanie elementów bezużytecznych w tle jest wykonywane na co najmniej jednym dedykowanym wątku, w zależności od tego, czy jest to tło czy serwer GC, i ma zastosowanie tylko do kolekcji generacji 2.

Wyrzucanie elementów bezużytecznych w tle jest domyślnie włączone. Można ją włączyć lub wyłączyć za pomocą ustawienia konfiguracji [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) w aplikacjach .NET Framework lub ustawienia [System. GC. współbieżne](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) w aplikacjach .NET Core.

> [!NOTE]
> Wyrzucanie elementów bezużytecznych w tle zastępuje [współbieżne odzyskiwanie pamięci](#concurrent-garbage-collection) i jest dostępne w .NET Framework 4 i nowszych wersjach. W .NET Framework 4 jest obsługiwana tylko dla wyrzucania elementów bezużytecznych *stacji roboczej* . Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych w tle jest dostępne zarówno dla *stacji roboczej* , jak i *serwera* .

Kolekcja tymczasowych generacji podczas wyrzucania elementów bezużytecznych w tle jest znana jako wyrzucanie elementów bezużytecznych *pierwszego planu* . Gdy wystąpią wyrzucanie elementów bezużytecznych pierwszego planu, wszystkie zarządzane wątki są zawieszane.

Gdy wyrzucanie elementów bezużytecznych w tle jest w toku i przydzielono wystarczającą liczbę obiektów w generacji 0, środowisko CLR wykonuje wyrzucanie elementów bezużytecznych generacji 0 lub generacji 1. Nieznaczny wątek wyrzucania elementów bezużytecznych w tle sprawdza, czy występuje żądanie wyrzucania elementów bezużytecznych na pierwszym planie. Jeśli istnieje, kolekcja w tle zawiesza się tak, aby mogły wystąpić wyrzucanie elementów bezużytecznych na pierwszym planie. Po zakończeniu wyrzucania elementów bezużytecznych, dedykowane wątki wyrzucania elementów bezużytecznych w tle i wątki użytkownika są wznawiane.

Wyrzucanie elementów bezużytecznych w tle usuwa ograniczenia alokacji narzucone przez współbieżne wyrzucanie elementów bezużytecznych, ponieważ tymczasowe wyrzucanie elementów bezużytecznych Wyrzucanie elementów bezużytecznych w tle umożliwia usuwanie martwych obiektów z generacji tymczasowych. Można również rozszerzyć stertę, jeśli jest to konieczne podczas wyrzucania elementów bezużytecznych generacji 1.

## <a name="background-workstation-vs-server-gc"></a>W tle stacja robocza a serwer GC

Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych w tle jest dostępne dla serwera GC. W tle jest domyślnym trybem odzyskiwania pamięci serwera.

Odzyskiwanie pamięci serwera w tle działa podobnie do wyrzucania elementów bezużytecznych stacji roboczej, ale istnieje kilka różnic:

- Wyrzucanie elementów bezużytecznych stacji roboczej w tle używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych w tle, podczas gdy odzyskiwanie pamięci serwera Zwykle istnieje dedykowany wątek dla każdego procesora logicznego.

- W przeciwieństwie do wątku wyrzucania elementów bezużytecznych w tle stacji roboczej serwer w tle nie przekracza limitu czasu.

Na poniższej ilustracji przedstawiono wyrzucanie elementów bezużytecznych *stacji roboczej* w tle wykonywane w osobnym, dedykowanym wątku:

![Wyrzucanie elementów bezużytecznych stacji roboczej](media/fundamentals/background-workstation-garbage-collection.png)

Na poniższej ilustracji przedstawiono wyrzucanie elementów bezużytecznych *serwera* w tle wykonywane w oddzielnych, dedykowanych wątkach:

![Odzyskiwanie pamięci serwera w tle](media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Jednoczesne wyrzucanie elementów bezużytecznych

> [!TIP]
> Ta sekcja ma zastosowanie do:
>
> - .NET Framework 3,5 i wcześniejszy dla wyrzucania elementów bezużytecznych stacji roboczych
> - .NET Framework 4 i starsze do wyrzucania elementów bezużytecznych serwera
>
> Współbieżne elementy bezużyteczne są zastępowane przez odzyskiwanie pamięci w tle w nowszych wersjach.

W systemie stacja robocza lub wyrzucanie elementów bezużytecznych serwera można [włączyć współbieżne wyrzucanie elementów bezużytecznych](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), dzięki czemu wątki mogą działać równolegle z dedykowanym wątkiem, który wykonuje wyrzucanie elementów bezużytecznych przez większość czasu trwania kolekcji. Ta opcja ma wpływ tylko na wyrzucanie elementów bezużytecznych w generacji 2; generacji 0 i 1 są zawsze niewspółbieżne, ponieważ kończą się szybko.

Współbieżne wyrzucanie elementów bezużytecznych umożliwia lepsze reagowanie aplikacji interaktywnych przez zminimalizowanie przerw w kolekcji. Zarządzane wątki mogą nadal uruchamiać większość czasu, gdy wątek współbieżnego odzyskiwania pamięci jest uruchomiony. Ten projekt skutkuje krótszymi pauzami podczas wyrzucania elementów bezużytecznych.

Współbieżne wyrzucanie elementów bezużytecznych jest wykonywane w ramach dedykowanego wątku. Domyślnie środowisko CLR uruchamia wyrzucanie elementów bezużytecznych stacji roboczej z włączonym współbieżnym wyrzucaniem elementów bezużytecznych na komputerach z jednym procesorem lub na wiele procesorów

Na poniższej ilustracji przedstawiono współbieżne wyrzucanie elementów bezużytecznych wykonywane w osobnym dedykowanym wątku.

![Współbieżne wątki odzyskiwania pamięci](media/gc-concurrent.png)

## <a name="see-also"></a>Zobacz też

- [Stacja robocza i odzyskiwanie pamięci serwera](workstation-server-gc.md)
- [Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md)
