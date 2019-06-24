---
title: Zmiana powodująca niezgodność, kategorie — .NET Core
description: Dowiedz się więcej o sposobach, w którym przełomowe zmiany są podzielone na platformie .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: 68cd3580e80305e54b41610f05d939a6aff8b54d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307506"
---
# <a name="breaking-change-categories"></a>Powodująca niezgodność kategorii zmian

*Zgodność* odwołuje się do możliwości kompilacji lub wykonania kodu na wersję implementacji .NET, innym niż za pomocą którego kod został pierwotnie opracowana. Określona zmiana może wpływać na zgodność na sześciu różnych sposobów. [Poszczególnych rodzaje zmian, które są uważane za podczas obliczania zgodności](index.md) można podzielić na pięć pierwszych kategorie. 

## <a name="behavioral-change"></a>Zmiana zachowania

Zmiana zachowania reprezentuje zmianę do zachowania elementu członkowskiego. Zmiany mogą być widoczne na zewnątrz (na przykład metoda może generować inny wyjątek,) lub może reprezentować, zmienione implementacji (na przykład zmiany w ten sposób jest obliczana wartość zwracana, dodawanie i usuwanie wywołań metody wewnętrznej, a nawet poprawa istotnie poprawiającą wydajność).

Podczas zmiany zachowania są widoczne na zewnątrz i modyfikować typu publicznego kontraktu, są one łatwe do oceny, ponieważ mają one wpływ na zgodność binarną. Implementacja zmiany są dużo bardziej skomplikowane ocenić; w zależności od charakteru zmiany i częstotliwość i wzorców użytkowania interfejsu API wpływ zmiany można dostosować w zakresie poważny do niewielkiej.  

## <a name="binary-compatibility"></a>Zgodność binarną

Zgodność binarną odnosi się do możliwości klienta interfejsu API za pomocą interfejsu API w nowszej wersji bez ponownej kompilacji. Zmiany, takie jak dodanie metody lub dodanie nowych implementacji interfejsu do typu nie wpływają na zgodność binarną. Jednak usunięcie lub zmienianie podpisów publicznych zestawu, aby konsumenci dłużej korzystać z tego samego interfejsu, które są udostępniane przez zestaw wpływać na zgodność binarną. Zmiana tego rodzaju jest określane jako *binarne niezgodna zmiana*.

## <a name="source-compatibility"></a>Zgodności źródła

 Źródło zgodność odnosi się do istniejących konsumentów interfejsu API możliwość ponownie skompilować użyciem nowszej wersji bez wprowadzania żadnych zmian źródła. A *źródła niezgodna zmiana* występuje, gdy konsument trzeba zmodyfikować kod źródłowy, aby pomyślnie algorytmie nowszą wersję interfejsu API.

## <a name="design-time-compatibility"></a>Zgodność czasie projektowania

Podczas projektowania zgodność odnosi się do zachowania środowiska czasu projektowania w różnych wersjach programu Visual Studio i innych środowisk w czasie projektowania. Chociaż może to obejmować zachowanie lub projektantów interfejsu użytkownika, najważniejszych aspektów projektowania zgodności dotyczy zgodności projektu. Projekt lub rozwiązanie musi mieć możliwość go otworzyć i używane w nowszej wersji środowiska czasu projektowania.

## <a name="backwards-compatibility"></a>Wstecznej zgodności

Wstecz zgodność odnosi się do możliwości konsumenta istniejącego interfejsu API w celu uruchomienia nowej wersji podczas zachowuje się w taki sam sposób. Zmiany zachowania i zmiany w zgodność binarną wpływa na wstecznej zgodności. Jeśli użytkownik nie będzie mógł uruchomić lub zachowuje się inaczej, gdy działających w odniesieniu do nowszej wersji interfejsu API, interfejs API jest *wstecz niezgodne*.

Zmiany wpływające na wstecznej zgodności są odradzane, ponieważ deweloperzy domyślnie oczekiwać wstecznej zgodności w nowszych wersjach interfejsu API.

## <a name="forward-compatibility"></a>Zgodność z nowszymi wersjami

Zgodność z nowszymi wersjami odnosi się do możliwości konsumenta istniejącego interfejsu API w celu uruchomienia starszej wersji podczas wykazujących takie samo zachowanie. Jeśli użytkownik nie będzie mógł uruchomić lub zachowuje się inaczej gdy wykonywane są starszej wersji interfejsu API, interfejs API jest *do przodu niezgodne*. 

Praktycznie zachowaniu zgodność z nowszymi wersjami wykluczającą zmiany lub dodatki wersji, ponieważ te zmiany uniemożliwić użytkownikowi, który jest przeznaczony dla nowszej wersji uruchamianie starszej wersji. Deweloperzy oczekują, że konsumenta, która opiera się na nowszych interfejsów API, mogą nie działać poprawnie przy użyciu starszych interfejsu API. 

Obsługa zgodność z nowszymi wersjami nie jest celem platformy .NET Core.

## <a name="see-also"></a>Zobacz także

[Oceń przełomowe zmiany w programie .NET Core](index.md)
