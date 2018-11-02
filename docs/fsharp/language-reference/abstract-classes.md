---
title: Klasy abstrakcyjne (F#)
description: 'Dowiedz się więcej o F # klas abstrakcyjnych, których pozostawienie niektórych lub wszystkich elementów członkowskich niezaimplementowane i reprezentują typowych funkcji różnorodnych typów obiektów.'
ms.date: 05/16/2016
ms.openlocfilehash: 7e1bb9daca7e8a3b442cd7fb02ef99bb6a2085cb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43745453"
---
# <a name="abstract-classes"></a>Klasy abstrakcyjne

*Klasy abstrakcyjne* są klasami, które opuszczają niektórych lub wszystkich elementów członkowskich niezaimplementowane, tak aby implementacji może być udostępniane przez klasy pochodne.

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

W programowanie zorientowane obiektowo, klasa abstrakcyjna służy jako klasa bazowa hierarchii i reprezentuje typowych funkcji różnorodnych typów obiektów. Jak sugeruje nazwa "abstract", klasy abstrakcyjne często nie odpowiadają bezpośrednio na konkretnej jednostki w domenie problem. Jednak reprezentują one wiele różnych jednostek konkretnych posiadane przez wspólne.

Klasy abstrakcyjne musi mieć `AbstractClass` atrybutu. Mogą mieć zaimplementowane i niezaimplementowane elementów członkowskich. Użycie terminów *abstrakcyjne* po zastosowaniu do klasy jest taka sama, jak w innych językach .NET; jednak użycie terminów *abstrakcyjne* po zastosowaniu do metody (i właściwości) różni się nieco w języku F # z jego Użyj w innych językach .NET. W języku F #, gdy metoda jest oznaczona atrybutem `abstract` — słowo kluczowe, oznacza to, czy element członkowski ma wpis, znane jako *wysyłania wirtualnego miejsca*, w tabeli wewnętrznej funkcji wirtualnych dla tego typu. Innymi słowy, ta metoda jest wirtualny, mimo że `virtual` — słowo kluczowe nie jest używany w języku F #. Słowo kluczowe `abstract` jest używana na metod wirtualnych, niezależnie od tego, czy metoda jest implementowana. Deklaracja gniazdo wirtualnego wysyłania różni się od definicji metody dla tego miejsca wysyłania. W związku z tym, F # odpowiednik metody wirtualnej deklaracji i definicji w innym języku .NET jest kombinacją zarówno w deklaracji metody abstrakcyjnej, jak i w oddzielnych definicji, z oboma `default` — słowo kluczowe lub `override` — słowo kluczowe. Aby uzyskać więcej informacji i przykładów, zobacz [metody](members/methods.md).

Klasa jest traktowany jako abstrakcyjne, tylko wtedy, gdy istnieją metody abstrakcyjne, które są zadeklarowane, ale nie zdefiniowane. W związku z tym nie zawsze abstrakcyjnych klas są klasami, które zawierają metody abstrakcyjne. Jeśli klasa ma niezdefiniowane metody abstrakcyjne, nie używaj **abstractclass —** atrybutu.

W poprzedniej składni *modyfikator dostępności* może być `public`, `private` lub `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](access-control.md).

Podobnie jak w przypadku innych typów abstrakcyjnych klas może mieć klasy bazowej i przynajmniej jedna podstawowa interfejsów. Każdej klasy bazowej lub interfejsu pojawia się w osobnym wierszu wraz z `inherit` — słowo kluczowe.

Definicja typu klasy abstrakcyjnej mogą zawierać elementy członkowskie w pełni zdefiniowana, ale może również zawierać abstrakcyjne składowe. Składnia abstrakcyjne składowe są pokazane osobno w poprzedniej składni. W tej składni *sygnatura typu* elementu członkowskiego jest lista, która zawiera parametr wpisuje kolejność i typy zwracane, oddzielone `->` tokeny i/lub `*` tokenów zgodnie z potrzebami dla przenoszeni i tupled Parametry. Składnia podpisy typu abstrakcyjnej składowej jest taka sama jak używane w plikach podpisu i wyświetlanych przez funkcję IntelliSense w edytorze kodu programu Visual Studio.

Poniższy kod ilustruje klasę abstrakcyjną kształtu, który ma dwie nieabstrakcyjnej klasy pochodne, kwadratu i okrąg. W przykładzie pokazano sposób użycia klasy abstrakcyjne, metod i właściwości. W tym przykładzie klasa abstrakcyjna kształt reprezentuje typowe elementy okrąg konkretnej jednostki i kwadrat. Często używane funkcje wszystkich kształtów (w dwuwymiarowej współrzędnych) zostały wyabstrahowane na zewnątrz do klasy kształtu: pozycji na siatce, kąt obrotu i właściwości pole i obwód. Te można przesłonić, z wyjątkiem pozycji zachowanie, którego nie można zmienić poszczególnych kształtów.

Metoda obrotu może zostać zastąpiona w jak klasa Circle jest obrót niezmiennej ze względu na jej symetrii. Dlatego w klasie okrąg metoda obrotu zastępuje metodę, która nie wykonuje żadnych działań.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Dane wyjściowe:**

```
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Zobacz także

- [Klasy](classes.md)
- [Elementy członkowskie](members/index.md)
- [Metody](members/methods.md)
- [Właściwości](members/Properties.md)
