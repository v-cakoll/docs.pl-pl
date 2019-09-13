---
title: C# odwołanie wirtualne
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 586e50818fc8ceaad5ca1925c0636b31015d81d4
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925373"
---
# <a name="virtual-c-reference"></a>virtual (odwołanie w C#)

`virtual` Słowo kluczowe jest używane do modyfikacji deklaracji metody, właściwości, indeksatora lub zdarzenia i umożliwia jej zastąpienie w klasie pochodnej. Na przykład ta metoda może zostać przesłonięta przez dowolną klasę, która ją dziedziczy:

```csharp
public virtual double Area() 
{
    return x * y;
}
```

Implementację wirtualnego elementu członkowskiego można zmienić przez [zastępujący element członkowski](override.md) w klasie pochodnej. Aby uzyskać więcej informacji na temat sposobu używania `virtual` słowa kluczowego, zobacz [przechowywanie wersji z przesłonięciami i nowymi słowami kluczowymi](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) i [wiedzą, kiedy używać przesłonięć i nowych słów kluczowych](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="remarks"></a>Uwagi

Gdy wywoływana jest metoda wirtualna, typ czasu wykonywania obiektu jest sprawdzany dla elementu członkowskiego, który jest zastępujący. Nadrzędny element członkowski w najbardziej pochodnej klasie jest wywoływany, który może być pierwotną składową, jeśli żadna Klasa pochodna nie przesłoni elementu członkowskiego.

Domyślnie metody nie są wirtualne. Nie można zastąpić metody innej niż wirtualna.

Nie `virtual` można użyć modyfikatora `abstract` `static`z modyfikatorami, `private`,, `override` lub. W poniższym przykładzie przedstawiono Właściwość wirtualną:

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

Właściwości wirtualne zachowują się jak metody abstrakcyjne, z wyjątkiem różnic w składni deklaracji i wywołania.

- Wystąpił błąd podczas używania `virtual` modyfikatora dla właściwości statycznej.

- Wirtualną Właściwość dziedziczoną można zastąpić w klasie pochodnej przez dołączenie deklaracji właściwości, która używa `override` modyfikatora.

## <a name="example"></a>Przykład

W tym przykładzie `Shape` Klasa zawiera dwie współrzędne `x`, `y`i `Area()` metodę wirtualną. Różne klasy kształtu, takie `Circle`jak `Cylinder`, i `Sphere` dziedziczą `Shape` klasę, a obszar powierzchni jest obliczany dla każdego rysunku. Każda klasa pochodna ma własną implementację `Area()`zastępującą.

Zwróć uwagę, że dziedziczone `Circle`klasy `Sphere`, i `Cylinder` wszystkie używają konstruktorów, które inicjują klasę bazową, jak pokazano w poniższej deklaracji.

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

Poniższy program oblicza i wyświetla odpowiedni obszar dla każdego rysunku przez wywoływanie odpowiedniej implementacji `Area()` metody, zgodnie z obiektem, który jest skojarzony z metodą.

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Polimorfizm](../../programming-guide/classes-and-structs/polymorphism.md)
- [abstract](abstract.md)
- [override](override.md)
- [New (modyfikator)](new-modifier.md)
