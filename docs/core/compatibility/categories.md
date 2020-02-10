---
title: Kategorie zmian powodujących niezgodność
description: Dowiedz się więcej na temat sposobu kategoryzowania istotnych zmian w programie .NET Core.
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093048"
---
# <a name="breaking-change-categories"></a>Kategorie zmian powodujących niezgodność

*Zgodność* odnosi się do możliwości kompilowania lub wykonywania kodu w wersji implementacji platformy .NET innej niż ta, z którą pierwotnie opracowano kod. Konkretna zmiana może mieć wpływ na zgodność na sześć różnych sposobów. [Poszczególne rodzaje zmian](index.md) , które są brane pod uwagę podczas oceny zgodności, znajdują się w następujących kategoriach:

- [zmiana zachowania](#behavioral-change)
- [zgodność binarna](#binary-compatibility)
- [zgodność ze źródłem](#source-compatibility)
- [zgodność czasu projektowania](#design-time-compatibility)
- [zgodność z poprzednimi wersjami](#backwards-compatibility)
- [zgodność do przodu](#forward-compatibility) (nie jest celem programu .NET Core)

## <a name="behavioral-change"></a>Zmiana zachowania

Zmiana behawioralna reprezentuje zmianę zachowania elementu członkowskiego. Zmiana może być widoczna na zewnątrz (na przykład metoda może zgłosić inny wyjątek) lub może reprezentować zmienioną implementację (na przykład zmianę w sposobie obliczania wartości zwracanej, dodanie lub usunięcie wywołań metody wewnętrznej lub nawet znaczący wzrost wydajności).

Gdy zmiany behawioralne są widoczne na zewnątrz i modyfikują publiczną umowę typu, można je łatwo oszacować, ponieważ wpływają na zgodność binarną. Zmiany implementacji są znacznie trudniejsze do oszacowania; w zależności od rodzaju zmiany i częstotliwości i wzorców używania interfejsu API, wpływ zmiany może przedziały od pozostałej do niewielkiej ilości.

## <a name="binary-compatibility"></a>Zgodność binarna

Zgodność binarna odnosi się do zdolności konsumenta interfejsu API do korzystania z interfejsu API w nowszej wersji bez ponownej kompilacji. Takie zmiany jak dodanie metod lub dodanie nowej implementacji interfejsu do typu nie wpływa na zgodność binarną. Jednak usunięcie lub zmiana podpisów publicznych zestawu w taki sposób, aby klienci nie mogli już uzyskiwać dostępu do tego samego interfejsu uwidocznionego przez zestaw, ma wpływ na zgodność binarną. Zmiana tego rodzaju jest określana jako *binarna niezgodna zmiana*.

## <a name="source-compatibility"></a>Zgodność ze źródłem

Zgodność ze źródłem dotyczy możliwości istniejących odbiorców interfejsu API w celu ponownego skompilowania do nowszej wersji bez żadnych zmian źródłowych. *Niezgodna zmiana źródła* występuje, gdy konsument musi zmodyfikować kod źródłowy, aby pomyślnie skompilować go do nowszej wersji interfejsu API.

## <a name="design-time-compatibility"></a>Zgodność czasu projektowania

Zgodność czasu projektowania odnosi się do zachowania środowiska czasu projektowania między wersjami programu Visual Studio i innymi środowiskami czasu projektowania. Chociaż może to wiązać się z zachowaniem lub interfejsem użytkownika projektantów, najważniejszym aspektem zgodności w czasie projektowania jest zgodność projektów. Projekt lub rozwiązanie musi być możliwe do otwarcia i użycia w nowszej wersji środowiska czasu projektowania.

## <a name="backwards-compatibility"></a>Zgodność z poprzednimi wersjami

Zgodność z poprzednimi wersjami odnosi się do zdolności klienta interfejsu API do uruchamiania w nowej wersji, zachowując się w ten sam sposób. Obie zmiany w zachowaniu i zmiany w zgodności binarnej wpływają na zgodność z poprzednimi wersjami. Jeśli klient nie może działać lub działa inaczej w przypadku uruchamiania w nowszej wersji interfejsu API, interfejs API nie jest *zgodny z poprzednimi*wersjami.

Zmiany wpływające na zgodność z poprzednimi wersjami nie są zalecane, ponieważ deweloperzy oczekują wstecznej zgodności w nowszych wersjach interfejsu API.

## <a name="forward-compatibility"></a>Zgodność dalej

Zgodność ze starszymi wersjami odnosi się do zdolności klienta interfejsu API do uruchamiania w starszej wersji, przy jednoczesnym zachowaniu tego samego zachowania. Jeśli użytkownik nie może uruchomić lub działa inaczej w przypadku uruchamiania w starszej wersji interfejsu API, interfejs API nie jest *zgodny*.

Utrzymywanie zgodności w sposób niemal wyklucza wszelkie zmiany lub dodatki z wersji do wersji, ponieważ te zmiany uniemożliwiają uruchomienie odbiorcy, który jest przeznaczony dla nowszej wersji w ramach wcześniejszej wersji. Deweloperzy oczekują, że klient korzystający z nowszego interfejsu API może nie działać prawidłowo w porównaniu ze starszym interfejsem API.

Utrzymanie zgodności nie jest celem platformy .NET Core.

## <a name="see-also"></a>Zobacz też

- [Oszacowanie istotnych zmian w programie .NET Core](index.md)
