---
title: Stacja robocza a wyrzucanie elementów bezużytecznych serwera (GC)
description: Dowiedz się więcej o śmietniku stacji roboczej i serwera w .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103556"
---
# <a name="workstation-and-server-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczych i serwera

Moduł zbierający elementy bezużyteczne jest samoczyszczenia i może pracować w wielu różnych scenariuszach. Można jednak [ustawić typ wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) na podstawie cech obciążenia. Program CLR udostępnia następujące typy wyrzucania elementów bezużytecznych:

- Wyrzucanie elementów bezużytecznych stacji roboczych (GC), który jest przeznaczony dla aplikacji klienckich. Jest to domyślny smak GC dla autonomicznych aplikacji. W przypadku hostowanych aplikacji, na przykład tych obsługiwanych przez ASP.NET, host określa domyślny smak GC.

  Wyrzucanie elementów bezużytecznych stacji roboczej może być równoczesne lub niebieżne. Równoczesnych (lub *tła)* wyrzucania elementów bezużytecznych umożliwia zarządzanych wątków, aby kontynuować operacje podczas wyrzucania elementów bezużytecznych. [Wyrzucanie elementów bezużytecznych tła](background-gc.md) zastępuje [równoczesnych wyrzucania elementów bezużytecznych](background-gc.md#concurrent-garbage-collection) w .NET Framework 4 i nowszych wersjach.

- Wyrzucanie elementów bezużytecznych serwera, który jest przeznaczony dla aplikacji serwera, które wymagają wysokiej przepływności i skalowalności.

  - W .NET Core wyrzucanie elementów bezużytecznych serwera może być niebieżne lub tła.

  - W .NET Framework 4.5 i nowszych wersjach wyrzucanie elementów bezużytecznych serwera może być równoczesne lub tła. W .NET Framework 4 i poprzednich wersjach wyrzucanie elementów bezużytecznych serwera nie jest równoczesne.

Na poniższej ilustracji przedstawiono dedykowane wątki, które wykonują wyrzucania elementów bezużytecznych na serwerze:

![Wątki wyrzucania elementów bezużytecznych serwera](./media/gc-server.png)

## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności

### <a name="workstation-gc"></a>Stacja robocza GC

Poniżej przedstawiono zagadnienia dotyczące wątków i wydajności dla wyrzucania elementów bezużytecznych stacji roboczej:

- Kolekcja występuje w wątku użytkownika, który wyzwolił wyrzucania elementów bezużytecznych i pozostaje w tym samym priorytecie. Ponieważ wątki użytkownika zazwyczaj działają z normalnym priorytetem, moduł zbierający elementy bezużyteczne (który działa na wątku o normalnym priorytecie) musi konkurować z innymi wątkami dla czasu procesora CPU. (Wątki, które uruchamiają kod macierzysty nie są zawieszone na serwerze lub stacji roboczej wyrzucania elementów bezużytecznych.)

- Wyrzucanie elementów bezużytecznych stacji roboczej jest zawsze używane na komputerze, który ma tylko jeden procesor, niezależnie od [ustawienia konfiguracji](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

### <a name="server-gc"></a>GC serwera

Poniżej przedstawiono zagadnienia dotyczące wątków i wydajności dla wyrzucania elementów bezużytecznych serwera:

- Kolekcja występuje na wielu dedykowanych wątków, które są uruchomione na `THREAD_PRIORITY_HIGHEST` poziomie priorytetu.

- Sterta i dedykowany wątek do wykonywania wyrzucania elementów bezużytecznych są dostarczane dla każdego procesora CPU, a sterty są zbierane w tym samym czasie. Każdy stos zawiera stertę małych obiektów i sterty dużego obiektu, a wszystkie sterty są dostępne za pomocą kodu użytkownika. Obiekty na różnych stertach mogą odnosić się do siebie nawzajem.

- Ponieważ wiele wątków wyrzucania elementów bezużytecznych działa ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych na tym samym rozmiarze stosu.

- Wyrzucanie elementów bezużytecznych serwera często ma większe segmenty rozmiaru. Jest to jednak tylko uogólnienie: rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie. Nie należy zakładać rozmiar segmentów przydzielonych przez moduł zbierający elementy bezużyteczne podczas dostrajania aplikacji.

- Wyrzucanie elementów bezużytecznych serwera może być intensywnie korzystające z zasobów. Załóżmy na przykład, że istnieje 12 procesów, które używają gc serwera uruchomionego na komputerze, który ma cztery procesory. Jeśli wszystkie procesy zdarzyć się zbierać śmieci w tym samym czasie, będą kolidować ze sobą, jak nie byłoby 12 wątków zaplanowanych na tym samym procesorze. Jeśli procesy są aktywne, nie jest dobrym pomysłem, aby wszystkie one używać gc serwera.

Jeśli używasz setki wystąpień aplikacji, należy rozważyć użycie wyrzucania elementów bezużytecznych stacji roboczej z równoczesnym wyrzucaniem elementów bezużytecznych wyłączone. Spowoduje to mniej przełączania kontekstu, co może poprawić wydajność.

## <a name="see-also"></a>Zobacz też

- [Wyrzucanie elementów bezużytecznych w tle](background-gc.md)
- [Opcje konfiguracji w czasie wykonywania wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md)
