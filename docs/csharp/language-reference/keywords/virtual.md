---
title: wirtualny - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: eede3359b195661ff89a387e9b226bc970c27942
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612579"
---
# <a name="virtual-c-reference"></a>virtual (odwołanie w C#)

`virtual` Słowo kluczowe jest używane do modyfikowania deklaracji metody, właściwości, indeksatora lub zdarzenia i umożliwia jej zastąpienie w klasie pochodnej. Na przykład tej metody może zostać przesłonięta przez wszystkie klasy, która dziedziczy on:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Implementacja członka wirtualnego mogą zostać zmienione przez [zastępującej składowej](override.md) w klasie pochodnej. Aby uzyskać więcej informacji o sposobie używania `virtual` — słowo kluczowe, zobacz [przechowywanie wersji przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [, wiedząc, gdy Użyj zastępowania i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Uwagi

Po wywołaniu metody wirtualnej typu run-time obiektu jest sprawdzane pod kątem zastępującej składowej. Zastępującej składowej w klasie najbardziej pochodnej jest wywoływana, który może być oryginalnego elementu członkowskiego, jeśli nie Klasa pochodna przesłoniła elementu członkowskiego.

Domyślnie metody są inne niż wirtualny. Nie można zastąpić metody niewirtualnej.

Nie można użyć `virtual` modyfikator z `static`, `abstract`, `private`, lub `override` modyfikatorów. Właściwość wirtualną można znaleźć w poniższym przykładzie:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Właściwości wirtualne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywoływania.

- Jest to błąd, aby użyć `virtual` modyfikator na właściwość statyczna.

- Wirtualne właściwość dziedziczona może zostać przesłonięta w klasie pochodnej przez tym deklaracja właściwości, która używa `override` modyfikator.

## <a name="example"></a>Przykład

W tym przykładzie `Shape` klasa zawiera dwie współrzędne `x`, `y`i `Area()` metodę wirtualną. Klasy innego kształtu, takie jak `Circle`, `Cylinder`, i `Sphere` dziedziczą `Shape` klasy i obszar powierzchni jest obliczana dla każdego elementu. Każda klasa pochodna ma własną implementację zastąpienie `Area()`.

Należy zauważyć, że klasy dziedziczone `Circle`, `Sphere`, i `Cylinder` używają konstruktorów, które inicjowania klasy bazowej, jak pokazano w poniższej deklaracji.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Następujący program oblicza i wyświetla odpowiedni obszar dla każdego elementu przez wywołanie odpowiedniej implementacji `Area()` metodę, zgodnie z obiektu, który jest skojarzony z metodą.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Modyfikatory](modifiers.md)
- [Słowa kluczowe języka C#](index.md)
- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [new](new.md)