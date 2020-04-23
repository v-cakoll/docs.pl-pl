---
title: Wyrzucanie elementów bezużytecznych w tle
description: Dowiedz się więcej o wyrzucaniu elementów bezużytecznych w tle w .NET i o tym, jak różni się ona w zakresie wyrzucania elementów bezużytecznych na stacjach roboczych i serwerach.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103563"
---
# <a name="background-garbage-collection"></a>Wyrzucanie elementów bezużytecznych w tle

W tle wyrzucania elementów bezużytecznych (GC), efemeryczne generacji (0 i 1) są zbierane w razie potrzeby, podczas gdy kolekcja generacji 2 jest w toku. Wyrzucanie elementów bezużytecznych w tle jest wykonywane na co najmniej jeden dedykowany wątki, w zależności od tego, czy jest to tło lub serwer GC i dotyczy tylko kolekcji generacji 2.

Tło wyrzucania elementów bezużytecznych jest domyślnie włączona. Można go włączyć lub wyłączyć za pomocą ustawienia konfiguracji [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) w aplikacjach .NET Framework lub ustawienia [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) w aplikacjach .NET Core.

> [!NOTE]
> Wyrzucanie elementów bezużytecznych tła zastępuje [równoczesne wyrzucanie elementów bezużytecznych](#concurrent-garbage-collection) i jest dostępne w .NET Framework 4 i nowszych wersjach. W .NET Framework 4 jest obsługiwany tylko dla wyrzucania elementów *bezużytecznych stacji roboczej.* Począwszy od programu .NET Framework 4.5, wyrzucanie elementów bezużytecznych w tle jest dostępne zarówno dla *stacji roboczej,* jak i dla wyrzucania elementów bezużytecznych *serwera.*

Kolekcja na efemeryczne generacji podczas wyrzucania elementów *bezużytecznych tła* jest znany jako pierwszego planu wyrzucania elementów bezużytecznych. Gdy wystąpią wyrzucanie elementów bezużytecznych na pierwszym planie, wszystkie wątki zarządzane są zawieszone.

Gdy wyrzucanie elementów bezużytecznych tła jest w toku i zostały przydzielone wystarczającej liczby obiektów w generacji 0, CLR wykonuje generacji 0 lub generacji 1 pierwszego planu wyrzucania elementów bezużytecznych. Dedykowany wątek wyrzucania elementów bezużytecznych w tle sprawdza w częstych bezpiecznych punktach, aby ustalić, czy istnieje żądanie wyrzucania elementów bezużytecznych na pierwszym planie. Jeśli istnieje, kolekcja w tle zawiesza się tak, że na pierwszym planie wyrzucania elementów bezużytecznych może wystąpić. Po zakończeniu wyrzucania elementów bezużytecznych na pierwszym planie, dedykowane wątki wyrzucania elementów bezużytecznych tła i wątki użytkownika wznowić.

Tło wyrzucania elementów bezużytecznych usuwa ograniczenia alokacji nałożone przez równoczesnych wyrzucania elementów bezużytecznych, ponieważ efemeryczne wyrzucania elementów bezużytecznych może wystąpić podczas wyrzucania elementów bezużytecznych w tle. Tło wyrzucania elementów bezużytecznych można usunąć martwe obiekty w efemeryczne pokolenia. Można również rozwinąć stos, jeśli jest to konieczne podczas wyrzucania elementów bezużytecznych generacji 1.

## <a name="background-workstation-vs-server-gc"></a>Stacja robocza w tle a gc serwera

Począwszy od programu .NET Framework 4.5, wyrzucanie elementów bezużytecznych w tle jest dostępne dla gc serwera. GC w tle jest domyślnym trybem wyrzucania elementów bezużytecznych serwera.

Funkcje wyrzucania elementów bezużytecznych serwera w tle, podobnie jak wyrzucanie elementów bezużytecznych na stacji roboczej w tle, ale istnieje kilka różnic:

- Tło stacji elementów bezużytecznych używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych tła, podczas gdy serwer w tle wyrzucania elementów bezużytecznych używa wielu wątków. Zazwyczaj istnieje dedykowany wątek dla każdego procesora logicznego.

- W przeciwieństwie do wątku wyrzucania elementów bezużytecznych tła stacji roboczej wątki GC serwera tła nie limit czasu.

Na poniższej ilustracji przedstawiono wyrzucanie elementów *bezużytecznych stacji roboczej* w tle wykonywane na oddzielnym, dedykowanym wątku:

![Wyrzucanie elementów bezużytecznych stacji roboczej w tle](./media/fundamentals/background-workstation-garbage-collection.png)

Na poniższej ilustracji przedstawiono wyrzucanie elementów bezużytecznych *serwera* w tle wykonywane na oddzielnych, dedykowanych wątkach:

![Wyrzucanie elementów bezużytecznych serwera w tle](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Równoczesne wyrzucanie elementów bezużytecznych

> [!TIP]
> Niniejsza sekcja dotyczy:
>
> - .NET Framework 3.5 i starsze dla wyrzucania elementów bezużytecznych stacji roboczych
> - .NET Framework 4 i starsze dla wyrzucania elementów bezużytecznych serwera
>
> Równoczesnych elementów bezużytecznych jest zastępowany przez tło wyrzucania elementów bezużytecznych w nowszych wersjach.

Na stacji roboczej lub serwera wyrzucania elementów bezużytecznych, można [włączyć równoczesnych wyrzucania elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), co umożliwia wątki do uruchamiania jednocześnie z dedykowanym wątku, który wykonuje wyrzucania elementów bezużytecznych przez większość czasu trwania kolekcji. Ta opcja dotyczy tylko wyrzucania elementów bezużytecznych w generacji 2; pokolenia 0 i 1 są zawsze niebieżne, ponieważ kończą się szybko.

Równoczesnych wyrzucania elementów bezużytecznych umożliwia interaktywne aplikacje, aby być bardziej elastyczne, minimalizując pauzy dla kolekcji. Zarządzane wątki można nadal działać przez większość czasu, gdy jest uruchomiony wątek równoczesnych wyrzucania elementów bezużytecznych. Powoduje to krótsze pauzy, gdy występuje wyrzucanie elementów bezużytecznych.

Równoczesnych wyrzucania elementów bezużytecznych jest wykonywana na dedykowany wątek. Domyślnie program CLR uruchamia wyrzucanie elementów bezużytecznych na stacjach roboczych z równoczesnym wyrzucaniem elementów bezużytecznych włączonym zarówno na komputerach jednoprocesorowych, jak i wieloprocesorowych.

Na poniższej ilustracji przedstawiono równoczesnych wyrzucania elementów bezużytecznych wykonywane na oddzielny wątek dedykowany.

![Równoczesne wątki wyrzucania elementów bezużytecznych](./media/gc-concurrent.png)

## <a name="see-also"></a>Zobacz też

- [Wyrzucanie elementów bezużytecznych stacji roboczych i serwera](workstation-server-gc.md)
- [Opcje konfiguracji w czasie wykonywania wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md)
