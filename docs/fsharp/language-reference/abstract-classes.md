---
title: Klasy abstrakcyjne
description: Dowiedz F# się więcej na temat klas abstrakcyjnych, które opuszczają niektóre lub wszystkie elementy członkowskie niezaimplementowane i reprezentujące wspólną funkcjonalność różnorodnych typów obiektów.
ms.date: 05/16/2016
ms.openlocfilehash: d7fc87178cff7c5c824992c97198b49f87025f00
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082944"
---
# <a name="abstract-classes"></a>Klasy abstrakcyjne

*Klasy abstrakcyjne* to klasy, które opuszczają niektóre lub wszystkie składowe niezaimplementowane, dzięki czemu implementacje mogą być dostarczane przez klasy pochodne.

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

W programowaniu zorientowanym obiektowo Klasa abstrakcyjna jest używana jako klasa bazowa hierarchii i reprezentuje wspólną funkcjonalność różnorodnych typów obiektów. Jako że nazwa "abstract" oznacza, klasy abstrakcyjne często nie odpowiadają bezpośrednio na konkretne jednostki w domenie problemu. Jednak reprezentują one wiele różnych konkretnych jednostek.

Klasy abstrakcyjne muszą mieć `AbstractClass` atrybut. Mogą mieć zaimplementowane i niezaimplementowane elementy członkowskie. Użycie *abstrakcyjnych* warunków w przypadku zastosowania do klasy jest takie samo jak w innych językach .NET; Jednak użycie metody *abstrakcyjnej* w przypadku zastosowania do metod (i właściwości) jest nieco inne w F# porównaniu z użyciem w innych językach .NET. W F#programie, gdy metoda jest oznaczona za pomocą `abstract` słowa kluczowego, oznacza to, że element członkowski ma wpis, znany jako *wirtualne miejsce wysyłki*, w wewnętrznej tabeli funkcji wirtualnych dla tego typu. Innymi słowy, metoda jest wirtualna, chociaż `virtual` słowo kluczowe nie jest używane w F# języku. Słowo kluczowe `abstract` jest używane w metodach wirtualnych bez względu na to, czy metoda jest zaimplementowana. Deklaracja wirtualnego gniazda wysyłania jest oddzielona od definicji metody dla tego gniazda wysyłania. W związku z F# tym odpowiednik deklaracji i definicji metody wirtualnej w innym języku .NET jest kombinacją deklaracji metody abstrakcyjnej i oddzielnej definicji ze `default` słowem kluczowym lub `override` słowem kluczowym. Aby uzyskać więcej informacji i przykładów, zobacz [metody](./members/methods.md).

Klasa jest uznawana za abstrakcyjną tylko wtedy, gdy istnieją metody abstrakcyjne, które są zadeklarowane, ale nie zdefiniowane. W związku z tym klasy, które mają metody abstrakcyjne, nie są klasami abstrakcyjnymi. Jeśli Klasa nie ma niezdefiniowanych metod abstrakcyjnych, nie należy używać atrybutu **AbstractClass** .

W poprzedniej składni *modyfikatora Accessibility* może mieć `public` `private` wartość lub `internal`. Aby uzyskać więcej informacji, zobacz [Access Control](access-control.md).

Podobnie jak w przypadku innych typów, klasy abstrakcyjne mogą mieć klasę bazową i jeden lub więcej interfejsów podstawowych. Każda klasa podstawowa lub interfejs pojawia się w osobnym wierszu razem ze `inherit` słowem kluczowym.

Definicja typu klasy abstrakcyjnej może zawierać w pełni zdefiniowane elementy członkowskie, ale może również zawierać abstrakcyjne elementy członkowskie. Składnia abstrakcyjnych elementów członkowskich jest wyświetlana osobno w poprzedniej składni. W tej składni *sygnatura typu* elementu członkowskiego jest listą zawierającą typy parametrów w kolejności i typy zwracane, oddzielone `->` tokenami i/lub `*` tokenami, zgodnie z potrzebami dla rozwinięte i parametrów krotek. Składnia sygnatur typu abstrakcyjnego elementu członkowskiego jest taka sama jak ta, która jest używana w plikach sygnatur i która jest wyświetlana przez funkcję IntelliSense w edytorze Visual Studio Code.

Poniższy kod ilustruje kształt klasy abstrakcyjnej, który ma dwie nieabstrakcyjne klasy pochodne, kwadrat i okrąg. W przykładzie pokazano, jak używać klas abstrakcyjnych, metod i właściwości. W przykładzie kształt klasy abstrakcyjnej reprezentuje wspólne elementy konkretnych jednostek, koło i kwadrat. Wspólne funkcje wszystkich kształtów (w dwuwymiarowym układzie współrzędnych) są wyodrębniane do klasy Shape: położenie w siatce, kąt obrotu oraz właściwości obszaru i obwodu. Można je zastąpić, z wyjątkiem pozycji, zachowanie, którego poszczególne kształty nie mogą zmienić.

Metodę obrotu można zastąpić, podobnie jak w klasie Circle, która ma wartość rotacja niezmiennej ze względu na jej symetrię. Dlatego w klasie Circle Metoda rotacji jest zastępowana przez metodę, która nic nie robi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2901.fs)]

**Dane wyjściowe:**

```console
Perimeter of square with side length 10.000000 is 40.000000
Circumference of circle with radius 5.000000 is 31.415927
Area of Square: 100.000000
Area of Circle: 78.539816
```

## <a name="see-also"></a>Zobacz także

- [Klasy](classes.md)
- [Elementy członkowskie](./members/index.md)
- [Metody](./members/methods.md)
- [Właściwości](./members/Properties.md)
