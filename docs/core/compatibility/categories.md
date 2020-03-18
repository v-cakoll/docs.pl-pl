---
title: Kategorie zmian powodujących niezgodność
description: Dowiedz się, w jaki sposób zmiany dotyczące łamania są podzielone na .NET Core.
ms.date: 06/10/2019
ms.openlocfilehash: b273ebbb82da803cde66ea34760aa1779c6c1ca5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093048"
---
# <a name="breaking-change-categories"></a>Kategorie zmian powodujących niezgodność

*Zgodność* odnosi się do możliwości kompilowania lub wykonywania kodu w wersji implementacji .NET innej niż ta, z którą kod został pierwotnie opracowany. Konkretna zmiana może mieć wpływ na zgodność na sześć różnych sposobów. [Poszczególne rodzaje zmian,](index.md) które są brane pod uwagę podczas oceny zgodności należą do następujących kategorii:

- [zmiana zachowania](#behavioral-change)
- [kompatybilność binarna](#binary-compatibility)
- [zgodność źródła](#source-compatibility)
- [kompatybilność w czasie projektowania](#design-time-compatibility)
- [kompatybilność wsteczna](#backwards-compatibility)
- [zgodność do przodu](#forward-compatibility) (nie jest celem programu .NET Core)

## <a name="behavioral-change"></a>Zmiana zachowań

Zmiana zachowania reprezentuje zmianę zachowania elementu członkowskiego. Zmiana może być widoczna zewnętrznie (na przykład metoda może zgłosić inny wyjątek) lub może reprezentować zmienioną implementację (na przykład zmianę sposobu obliczania wartości zwracanej, dodanie lub usunięcie wywołań metody wewnętrznej, a nawet znacznej poprawy wydajności).

Gdy zmiany behawioralne są widoczne zewnętrznie i zmodyfikować kontrakt publiczny typu, są one łatwe do oceny, ponieważ wpływają one na zgodność binarną. Zmiany we wdrażaniu są znacznie trudniejsze do oceny; w zależności od charakteru zmiany oraz częstotliwości i wzorców stosowania API, wpływ zmiany może wahać się od poważnego do nieszkodliwego.

## <a name="binary-compatibility"></a>Kompatybilność binarna

Zgodność binarna odnosi się do możliwości konsumenta interfejsu API do korzystania z interfejsu API w nowszej wersji bez ponownej kompilacji. Takie zmiany, jak dodawanie metod lub dodawanie nowej implementacji interfejsu do typu nie wpływają na zgodność binarną. Jednak usunięcie lub zmiana podpisów publicznych zestawu, tak aby konsumenci nie mogli już uzyskać dostępu do tego samego interfejsu udostępnianego przez zestaw ma wpływ na zgodność binarną. Zmiana tego rodzaju jest określana jako *zmiana niezgodna z binarną*.

## <a name="source-compatibility"></a>Zgodność źródła

Zgodność źródła odnosi się do możliwości istniejących konsumentów interfejsu API do ponownej kompilacji względem nowszej wersji bez żadnych zmian źródłowych. *Źródło niezgodne zmiany* występuje, gdy konsument musi zmodyfikować kod źródłowy dla niego pomyślnie utworzyć dla nowszej wersji interfejsu API.

## <a name="design-time-compatibility"></a>Kompatybilność w czasie projektowania

Zgodność w czasie projektowania odnosi się do zachowania środowiska w czasie projektowania w różnych wersjach programu Visual Studio i innych środowiskach czasu projektowania. Chociaż może to obejmować zachowanie lub interfejsu projektanta, najważniejszym aspektem zgodności w czasie projektowania dotyczy zgodności projektu. Projekt lub rozwiązanie musi być możliwe do otwarcia i użycia w nowszej wersji środowiska czasu projektowania.

## <a name="backwards-compatibility"></a>Zgodność z poprzednimi wersjami

Zgodność wsteczna odnosi się do możliwości istniejącego konsumenta interfejsu API do uruchamiania w nowej wersji podczas zachowywania się w ten sam sposób. Zarówno zmiany behawioralne, jak i zmiany w zgodności binarnej wpływają na zgodność z poprzednimi wersjami. Jeśli konsument nie może uruchomić lub zachowuje się inaczej podczas uruchamiania przeciwko nowszej wersji interfejsu API, interfejs API jest *niezgodny z poprzednimi wersjami*.

Zmiany, które wpływają na zgodność z poprzednimi wersjami są odradzane, ponieważ deweloperzy oczekują zgodności wstecznej w nowszych wersjach interfejsu API.

## <a name="forward-compatibility"></a>Zgodność z przyszłością

Zgodność z przesyłaniem dalej odnosi się do możliwości istniejącego konsumenta interfejsu API do uruchamiania w starszej wersji, podczas gdy wykazują to samo zachowanie. Jeśli konsument nie może uruchomić lub zachowuje się inaczej po uruchomieniu przeciwko starszej wersji interfejsu API, interfejs API jest *niezgodny z dalej.*

Utrzymanie zgodności do przodu praktycznie wyklucza wszelkie zmiany lub dodatki z wersji do wersji, ponieważ te zmiany uniemożliwiają konsumentowi, który jest przeznaczony dla nowszej wersji, jest uruchomiony w starszej wersji. Deweloperzy oczekują, że konsument, który opiera się na nowszym interfejsie API może nie działać poprawnie w stosunku do starszego interfejsu API.

Utrzymanie zgodności z przesyłaniem dalej nie jest celem programu .NET Core.

## <a name="see-also"></a>Zobacz też

- [Ocena zmian w programach .NET Core](index.md)
