---
title: Tablice jednowymiarowe — Przewodnik programowania w języku C#
description: Utwórz tablicę jednowymiarową w języku C# przy użyciu operatora new określającego typ elementu tablicy i liczbę elementów.
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474595"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tablice jednowymiarowe (Przewodnik programowania w języku C#)

Można utworzyć tablicę jednowymiarową przy użyciu operatora [New](../../language-reference/operators/new-operator.md) określającego typ elementu tablicy oraz liczbę elementów. Poniższy przykład deklaruje tablicę pięciu liczb całkowitych:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

Ta tablica zawiera elementy z elementu `array[0]` do `array[4]` . Elementy tablicy są inicjowane do wartości domyślnej typu elementu, `0` dla liczb całkowitych.

W tablicach mogą być przechowywane elementy określonego typu, takie jak Poniższy przykład, który deklaruje tablicę ciągów:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a>Inicjowanie tablicy

Można zainicjować elementy tablicy, gdy deklarujesz tablicę. Specyfikator długości nie jest wymagany, ponieważ jest wywnioskowany przez liczbę elementów na liście inicjalizacji. Na przykład:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

Poniższy kod przedstawia deklarację tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
Można uniknąć `new` wyrażenia i typu tablicy podczas inicjowania tablicy po deklaracji, jak pokazano w poniższym kodzie. Ta nazwa jest nazywana [niejawnie wpisaną tablicą](implicitly-typed-arrays.md):

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

Można zadeklarować zmienną tablicową bez jej tworzenia, ale należy użyć operatora, `new` gdy przypiszesz nową tablicę do tej zmiennej. Na przykład:

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a>Typ wartości i tablice typów referencyjnych

Rozważmy następującą deklarację tablicy:  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

Wynik tej instrukcji zależy od tego, czy `SomeType` jest typem wartości czy typem referencyjnym. Jeśli jest to typ wartości, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy ma typ `SomeType` . Jeśli `SomeType` jest typem referencyjnym, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy jest zainicjowany do odwołania o wartości null. W obu wystąpieniach elementy są inicjowane do wartości domyślnej dla typu elementu. Aby uzyskać więcej informacji na temat typów wartości i typów referencyjnych, zobacz [typy wartości](../../language-reference/builtin-types/value-types.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Tablice](./index.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
