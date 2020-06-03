---
title: Stacja robocza a wyrzucanie elementów bezużytecznych serwera (GC)
description: Informacje o stacjach roboczych i wyrzucaniu elementów bezużytecznych serwera w programie .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 5ff2b1fe2f997913e071f35ec5abb167ed757608
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306698"
---
# <a name="workstation-and-server-garbage-collection"></a>Stacja robocza i odzyskiwanie pamięci serwera

Moduł wyrzucania elementów bezużytecznych jest samodostrajania i może współpracować w wielu różnych scenariuszach. Można jednak [ustawić typ wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) na podstawie charakterystyki obciążenia. Środowisko CLR udostępnia następujące typy wyrzucania elementów bezużytecznych:

- Odzyskiwanie pamięci stacji roboczej (GC) przeznaczone dla aplikacji klienckich. Jest to domyślna wersja GC dla aplikacji autonomicznych. Na przykład w przypadku aplikacji hostowanych przez ASP.NET host Określa domyślną wersję GC.

  Wyrzucanie elementów bezużytecznych stacji roboczej może być współbieżne lub niewspółbieżne. Współbieżne (lub w *tle*) wyrzucanie elementów bezużytecznych umożliwia zarządzanym wątkom kontynuowanie operacji podczas odzyskiwania pamięci. [Wyrzucanie elementów bezużytecznych w tle](background-gc.md) zastępuje [współbieżne odzyskiwanie pamięci](background-gc.md#concurrent-garbage-collection) w .NET Framework 4 i nowszych wersjach.

- Odzyskiwanie pamięci serwera, które jest przeznaczone dla aplikacji serwerowych, które potrzebują dużej przepływności i skalowalności.

  - W programie .NET Core zbieranie elementów bezużytecznych serwera może być niewspółbieżne lub niezgodne.

  - W .NET Framework 4,5 i nowszych wersjach zbieranie elementów bezużytecznych serwera może być niewspółbieżne lub niezgodne. W .NET Framework 4 i poprzednich wersjach zbieranie elementów bezużytecznych serwera nie jest współbieżne.

Na poniższej ilustracji przedstawiono dedykowane wątki, które wykonują wyrzucanie elementów bezużytecznych na serwerze:

![Wątki odzyskiwania pamięci serwera](media/gc-server.png)

## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności

### <a name="workstation-gc"></a>Stacja robocza GC

Poniżej przedstawiono zagadnienia dotyczące wątkowości i wydajności dotyczące wyrzucania elementów bezużytecznych stacji roboczej:

- Kolekcja odbywa się w wątku użytkownika, który wyzwolił wyrzucanie elementów bezużytecznych i pozostaje na tym samym priorytecie. Ponieważ wątki użytkownika zwykle działają przy normalnym priorytecie, Moduł wyrzucania elementów bezużytecznych (który jest uruchamiany w wątku o normalnym priorytecie) musi konkurować z innymi wątkami czasu procesora CPU. (Wątki, które uruchamiają kod natywny nie są zawieszone na serwerze lub w wyrzucaniu elementów bezużytecznych stacji roboczych).

- Wyrzucanie elementów bezużytecznych stacji roboczej jest zawsze używane na komputerze z tylko jednym procesorem, niezależnie od [Ustawienia konfiguracji](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

### <a name="server-gc"></a>Serwer GC

Poniżej przedstawiono zagadnienia związane z wątkami i wydajnością dla wyrzucania elementów bezużytecznych serwera:

- Kolekcja odbywa się na wielu dedykowanych wątkach, które są uruchomione na `THREAD_PRIORITY_HIGHEST` poziomie priorytetu.

- Sterta i dedykowany wątek służący do wykonywania wyrzucania elementów bezużytecznych są udostępniane dla każdego procesora, a sterty są zbierane w tym samym czasie. Każda sterta zawiera niewielką stertę obiektu i stertę dużego obiektu, a wszystkie sterty są dostępne przez kod użytkownika. Obiekty na różnych stertach mogą odwoływać się do siebie nawzajem.

- Ponieważ wielokrotne wątki odzyskiwania pamięci współpracują ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych stacji roboczej.

- Wyrzucanie elementów bezużytecznych serwera często ma większe rozmiary segmentów. Jest to jednak tylko Generalizacja: rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie. Nie należy tworzyć założeń dotyczących rozmiaru segmentów przydzielonej przez moduł zbierający elementy bezużyteczne podczas dostrajania aplikacji.

- Zbieranie elementów bezużytecznych serwera może być czasochłonne. Załóżmy na przykład, że istnieją 12 procesów korzystających z serwera GC uruchomionego na komputerze, który ma cztery procesory. Jeśli wszystkie procesy mają w tym samym czasie zbierać elementy bezużyteczne, mogą one zakłócać sobie nawzajem, ponieważ na tym samym procesorze zaplanowano 12 wątków. Jeśli procesy są aktywne, nie jest dobrym pomysłem na korzystanie z serwera GC.

Jeśli używasz setek wystąpień aplikacji, rozważ użycie wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym współbieżnym wyrzucaniem elementów bezużytecznych. Spowoduje to przełączenie do mniej kontekstu, co może poprawić wydajność.

## <a name="see-also"></a>Zobacz też

- [Odzyskiwanie pamięci w tle](background-gc.md)
- [Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych](../../core/run-time-config/garbage-collector.md)
