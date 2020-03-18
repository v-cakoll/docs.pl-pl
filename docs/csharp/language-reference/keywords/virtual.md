---
title: virtual - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173461"
---
# <a name="virtual-c-reference"></a>virtual (odwołanie w C#)

Słowo `virtual` kluczowe służy do modyfikowania metody, właściwości, indeksatora lub deklaracji zdarzenia i zezwalania na jego zastępowanie w klasie pochodnej. Na przykład ta metoda może zostać zastąpiona przez dowolną klasę, która ją dziedziczy:

```csharp
public virtual double Area()
{
    return x * y;
}
```

Implementacja członka wirtualnego może zostać zmieniona przez [nadrzędny element członkowski](override.md) w klasie pochodnej. Aby uzyskać więcej informacji `virtual` na temat używania słowa kluczowego, zobacz [Przechowywanie wersji za pomocą słów kluczowych Zastępowania i Nowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) oraz Wiedza o [tym, kiedy należy używać zastępowania i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Uwagi

Po wywołaniu metody wirtualnej typ czasu wykonywania obiektu jest sprawdzany pod kątem nadrzędnego elementu członkowskiego. Nadrzędny element członkowski w klasie najbardziej pochodnej jest wywoływana, która może być oryginalny element członkowski, jeśli żadna klasa pochodna nie zastąpi elementu członkowskiego.

Domyślnie metody nie są wirtualne. Nie można zastąpić metody niewirtualnej.

Modyfikatora `virtual` nie `static`można `abstract` `private`używać `override` z modyfikatorem , , lub modyfikatorami. W poniższym przykładzie przedstawiono właściwość wirtualną:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Właściwości wirtualne zachowują się jak metody wirtualne, z wyjątkiem różnic w składni deklaracji i wywołania.

- Jest to błąd, `virtual` aby użyć modyfikatora we właściwości statycznej.

- Właściwość dziedziczona wirtualna może zostać zastąpiona w klasie `override` pochodnej przez uwzględnienie deklaracji właściwości, która używa modyfikatora.

## <a name="example"></a>Przykład

W tym przykładzie `Shape` klasa zawiera dwie `x` `y`współrzędne `Area()` , i metody wirtualnej. Różne klasy kształtów, `Sphere` takie `Shape` jak `Circle`, `Cylinder`i dziedziczą klasę, a powierzchnia jest obliczana dla każdej liczby. Każda klasa pochodna ma własną `Area()`implementację zastąpienia .

Należy zauważyć, że `Circle` `Sphere`odziedziczone klasy , i `Cylinder` wszystkie konstruktory użytkowania, które inicjują klasę podstawową, jak pokazano w poniższej deklaracji.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Poniższy program oblicza i wyświetla odpowiedni obszar dla każdej liczby, wywołując `Area()` odpowiednią implementację metody, zgodnie z obiektem skojarzonym z metodą.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
- [Abstrakcja](abstract.md)
- [override](override.md)
- [nowy (modyfikator)](new-modifier.md)
