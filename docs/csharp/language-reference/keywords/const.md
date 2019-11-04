---
title: const — słowo C# kluczowe-odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 81660e6a56efe5737600122d4ff7e182654f9a9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422893"
---
# <a name="const-c-reference"></a>const (odwołanie w C#)

Użyj słowa kluczowego `const`, aby zadeklarować pole stałe lub stałą lokalną. Pola stałe i zmienne lokalne nie są zmiennymi i nie mogą być modyfikowane. Stałe mogą być liczbami, wartościami logicznymi, ciągami lub odwołaniem o wartości null. Nie należy tworzyć stałej do reprezentowania informacji, które można zmienić w dowolnym momencie. Na przykład nie należy używać pola stałego do przechowywania ceny usługi, numeru wersji produktu ani nazwy marki firmy. Te wartości mogą ulec zmianie z upływem czasu, a ponieważ kompilatory propagują stałe, inne kod skompilowane z bibliotekami będzie musiały zostać ponownie skompilowane w celu wyświetlenia zmian. Zobacz również słowo kluczowe [ReadOnly](./readonly.md) . Na przykład:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Uwagi

Typ deklaracji stałej określa typ elementów członkowskich, które wprowadza deklaracja. Inicjator stałego lokalnego lub stałego pola musi być wyrażeniem stałym, które może być niejawnie konwertowane na typ docelowy.

Wyrażenie stałe jest wyrażeniem, które może być w pełni oceniane w czasie kompilacji. W związku z tym jedynymi możliwymi wartościami dla stałych typów referencyjnych są `string` i odwołanie o wartości null.

Deklaracja stałej może deklarować wiele stałych, takich jak:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

Modyfikator `static` jest niedozwolony w deklaracji stałej.

Stała może uczestniczyć w wyrażeniu stałym w następujący sposób:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> Słowo kluczowe [ReadOnly](./readonly.md) różni się od słowa kluczowego `const`. Pole `const` można zainicjować tylko w deklaracji pola. Pole `readonly` można zainicjować w deklaracji lub w konstruktorze. W związku z tym pola `readonly` mogą mieć różne wartości w zależności od użytego konstruktora. Ponadto, chociaż `const` pole jest stałą czasu kompilacji, pole `readonly` może być używane dla stałych w czasie wykonywania, jak w tym wierszu: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak używać stałych jako zmiennych lokalnych.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory](index.md)
- [readonly](./readonly.md)
