---
title: const — słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 812aeb331b6dd333075d19076a896246ecc5b374
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713679"
---
# <a name="const-c-reference"></a>const (odwołanie w C#)

`const` Słowo kluczowe służy do deklarowania stałego pola lub stałego lokalnego. Stałe pola i lokalne nie są zmiennymi i nie mogą być modyfikowane. Stałe mogą być liczbami, wartościami logicznymi, ciągami lub odwołaniem zerowym. Nie należy tworzyć stałą do reprezentowania informacji, które można oczekiwać, aby zmienić w dowolnym momencie. Na przykład nie używaj stałego pola do przechowywania ceny usługi, numeru wersji produktu ani nazwy firmy. Wartości te mogą się zmieniać wraz z uchwale, a kompilatory propagować stałe, inny kod skompilowany z bibliotek będzie musiał zostać ponownie skompilowany, aby zobaczyć zmiany. Zobacz też słowo kluczowe [tylko do odczytu.](./readonly.md) Przykład:

```csharp
const int X = 0;
public const double GravitationalConstant = 6.673e-11;
private const string ProductName = "Visual C#";
```

## <a name="remarks"></a>Uwagi

Typ stałej deklaracji określa typ elementów członkowskich, które wprowadza deklaracja. Iinicjator stałego pola lokalnego lub stałego musi być wyrażeniem stałym, które można niejawnie przekonwertować na typ docelowy.

Wyrażenie stałe jest wyrażeniem, które można w pełni ocenić w czasie kompilacji. W związku z tym jedynymi możliwymi `string` wartościami dla stałych typów odwołań są i odwołanie null.

Stała deklaracja może zadeklarować wiele stałych, takich jak:

```csharp
public const double X = 1.0, Y = 2.0, Z = 3.0;
```

Modyfikator `static` nie jest dozwolone w deklaracji stałej.

Stała może uczestniczyć w wyrażeniu stałym w następujący sposób:

```csharp
public const int C1 = 5;
public const int C2 = C1 + 100;
```

> [!NOTE]
> Słowo kluczowe tylko do `const` [odczytu](./readonly.md) różni się od słowa kluczowego. Pole `const` można zainicjować tylko w deklaracji pola. Pole `readonly` można zainicjować w deklaracji lub w konstruktorze. W `readonly` związku z tym pola mogą mieć różne wartości w zależności od konstruktora używane. Ponadto, mimo `const` że pole jest stałą `readonly` w czasie kompilacji, pole może być używane dla stałych czasu wykonywania, jak w tym wierszu:`public static readonly uint l1 = (uint)DateTime.Now.Ticks;`

## <a name="example"></a>Przykład

[!code-csharp[csrefKeywordsModifiers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#5)]

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak używać stałych jako zmiennych lokalnych.

[!code-csharp[csrefKeywordsModifiers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#6)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory](index.md)
- [Readonly](./readonly.md)
