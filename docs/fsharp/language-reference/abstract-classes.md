---
title: Klasy abstrakcyjne (F#)
description: 'Więcej informacji na temat języka F # klas abstrakcyjnych, które pozostaw niektóre lub wszystkie elementy członkowskie niezaimplementowane i reprezentują często używane funkcje zestaw typów obiektów.'
ms.date: 05/16/2016
ms.openlocfilehash: c472e9d164ae78bde716bb5102e54f4e698b61b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562393"
---
# <a name="abstract-classes"></a>Klasy abstrakcyjne

*Klasy abstrakcyjne* klas, które opuszczają niektóre lub wszystkie elementy członkowskie niezaimplementowane, dzięki czemu można podać implementacji klasy pochodne.

## <a name="syntax"></a>Składnia

```fsharp
// Abstract class syntax.
[<AbstractClass>]
type [ accessibility-modifier ] abstract-class-name =
[ inherit base-class-or-interface-name ]
[ abstract-member-declarations-and-member-definitions ]

// Abstract member syntax.
abstract member member-name : type-signature
```

## <a name="remarks"></a>Uwagi
W programowanie zorientowane obiektowo klasy abstrakcyjnej jest używany jako klasa podstawowa hierarchii i reprezentuje często używane funkcje zestaw typów obiektów. Jak nazwa "abstract" wskazuje, klas abstrakcyjnych często nie odpowiada bezpośrednio na konkretnych obiektów w domenie problem. Jednak reprezentują, co wiele różnych obiektów konkretnych mają wspólną.

Klasy abstrakcyjne muszą mieć `AbstractClass` atrybutu. Można mieć zaimplementowany i niezaimplementowane elementów członkowskich. Użycie warunku *abstrakcyjny* po zastosowaniu do klasy jest taka sama jak w innych językach .NET; jednak użycie terminu *abstrakcyjny* po zastosowaniu do metody (i właściwości) jest nieco inne w języku F # z jego Użyj innych języków platformy .NET. W języku F #, gdy metoda jest oznaczona atrybutem `abstract` — słowo kluczowe, to oznacza, że element członkowski ma wpis, znany jako *miejsca wysyłania wirtualnego*, w tabeli wewnętrznej funkcji wirtualnych dla tego typu. Innymi słowy, metoda jest wirtualny, mimo że `virtual` — słowo kluczowe nie jest używany w języku F #. Słowo kluczowe `abstract` jest używane w metodach wirtualnych niezależnie od tego, czy metoda jest zaimplementowana. Deklaracja miejsca wysyłania wirtualnego jest oddzielony od definicji metody dla tego gniazda wysyłania. W związku z tym F # odpowiednikiem metody wirtualnej deklaracji i definicji w innym języku .NET jest kombinacją zarówno w deklaracji metody abstrakcyjnej, jak i w oddzielnych definicji, przy użyciu jednej `default` — słowo kluczowe lub `override` — słowo kluczowe. Aby uzyskać dodatkowe informacje i przykłady, zobacz [metody](members/methods.md).

Klasa jest traktowany jako abstract, tylko wtedy, gdy istnieją metody abstrakcyjne, które są zadeklarowane, ale nie zdefiniowano. W związku z tym klas, które mają metody abstrakcyjne nie są zawsze abstrakcyjnej klasy. Jeśli klasa ma niezdefiniowane metody abstrakcyjne, nie używaj **AbstractClass** atrybutu.

W poprzednich składni *modyfikator dostępności* może być `public`, `private` lub `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md).

Podobnie jak w przypadku innych typów klas abstrakcyjnych może mieć klasy podstawowej i jeden lub więcej podstawowych interfejsów. Każdej klasy podstawowej lub interfejsu jest wyświetlany w osobnym wierszu razem z `inherit` — słowo kluczowe.

Definicja typu klasy abstrakcyjnej mogą zawierać członków całkowicie zdefiniowane, ale może również zawierać abstrakcyjne elementy członkowskie. Składnia abstrakcyjne elementy członkowskie jest wyświetlany osobno w poprzednim składni. W tej składni *podpis typu* elementu członkowskiego jest listę zawierającą parametr typy w kolejności i zwracane typy rozdzielone `->` tokeny i/lub `*` tokeny odpowiednio dla typu curried i spójnej kolekcji Parametry. Składnia podpisów typ abstrakcyjny element członkowski jest taka sama jak używane w plikach sygnatury i wyświetlanego przez funkcję IntelliSense w edytorze kodu programu Visual Studio.

Poniższy kod ilustruje kształtu, które ma dwa nieabstrakcyjnej klasy pochodne, kwadratowych i okrąg klasy abstrakcyjnej. W przykładzie dotyczące używania klas abstrakcyjnych, metod i właściwości. W tym przykładzie klasa ogólna kształtu reprezentuje typowe elementy okręgu konkretnych jednostek i kwadratowe. Wspólne funkcje wszystkich kształtów (w dwuwymiarowa współrzędnych) zamiast tego zostają wyodrębnione limit do klasy kształtu: pozycji na siatki, kąt obrotu i właściwości powierzchni i obwodu. Te można przesłonić, z wyjątkiem pozycji, działanie, którego nie można zmienić poszczególnych kształtów.

Można zastąpić metody obrotu, jak klasy koło, która jest obracanie niezmiennej ze względu na jego symetrycznego. Dlatego w klasie koło metody obrotu zastępuje metodę, która nie działa.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Dane wyjściowe:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Zobacz też
[Klasy](classes.md)

[Elementy członkowskie](members/index.md)

[Metody](members/methods.md)

[Właściwości](members/Properties.md)
