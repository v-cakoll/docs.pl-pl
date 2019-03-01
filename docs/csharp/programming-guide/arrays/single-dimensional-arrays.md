---
title: Tablice jednowymiarowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: d2ee0c2a38ffeef3d2d0b339b98e48c25227d96c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973265"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tablice jednowymiarowe (Przewodnik programowania w języku C#)

Można zadeklarować tablicy jednowymiarowej pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Ta tablica zawiera elementy z `array[0]` do `array[4]`. [Nowe](../../../csharp/language-reference/keywords/new.md) operator jest używany do utworzenia tablicy i Inicjowanie elementów tablicy, do wartości domyślnych. W tym przykładzie wszystkie elementy tablicy są inicjowane od zera.  
  
 Tablica, która przechowuje elementami typu ciąg może być zadeklarowana w taki sam sposób. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy

 Istnieje możliwość zainicjowania tablicy po zgłoszeniu, w którym to przypadku specyfikator długości nie jest potrzebna, ponieważ jest już podana przez liczbę elementów listy inicjowania. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Tablica ciągów mogą być inicjowane w taki sam sposób. Poniżej przedstawiono deklaracją tablicy ciągów gdzie każdy element tablicy jest inicjowany przez nazwę dnia:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Podczas inicjowania tablicy po deklaracji, można użyć następujących skrótów klawiaturowych:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Można zadeklarować zmiennej tablicy bez inicjowania, ale muszą używać `new` operator podczas przypisywania tablicy do tej zmiennej. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 wprowadzono niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ wartości i tablicami typu odwołania

 Rozważmy następującą deklarację tablicy:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Wynikiem tej instrukcji jest zależna od tego, czy `SomeType` jest typem wartości lub typem referencyjnym. Jeśli jest to typ wartości, instrukcja tworzy tablicę 10 elementów, z których każdy ma typ `SomeType`. Jeśli `SomeType` jest typem referencyjnym instrukcja tworzy tablicę o 10 elementów, z których każdy jest zainicjowany na odwołanie o wartości null.  
  
 Aby uzyskać więcej informacji dotyczących typów wartości i typami odwołania, zobacz [typy](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Tablice](../../../csharp/programming-guide/arrays/index.md)
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
