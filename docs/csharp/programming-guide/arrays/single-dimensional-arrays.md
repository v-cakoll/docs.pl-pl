---
title: Tablice jednowymiarowe (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313956"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tablice jednowymiarowe (Przewodnik programowania w języku C#)
Można zadeklarować tablicy jednowymiarowej pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 Ta tablica zawiera elementy z `array[0]` do `array[4]`. [Nowe](../../../csharp/language-reference/keywords/new.md) operator jest używany do utworzenia tablicy i zainicjować elementów tablicy do wartości domyślnych. W tym przykładzie wszystkie elementy tablicy są inicjowane od zera.  
  
 Tablica, która przechowuje elementy parametry mogą być deklarowane w taki sam sposób. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy  
 Można zainicjować tablicy po deklaracji, w którym to przypadku specyfikator rangi nie jest potrzebna, ponieważ jest już podana przez liczbę elementów na liście inicjowania. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 W ten sam sposób można zainicjować tablicy ciągów. Oto deklarację tablicy ciągów której każdy element tablicy jest inicjowany przez nazwę dnia:  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 Podczas inicjowania tablicy po deklaracji, można użyć następujących skrótów klawiaturowych:  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 Można zadeklarować zmiennej tablicowej bez inicjowania, ale muszą używać `new` operator podczas przypisywania tablicą do tej zmiennej. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 C# 3.0 wprowadzono niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ wartości i tablic typu odwołania  
 Należy wziąć pod uwagę następujące oświadczenie tablicy:  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 Wynik tej instrukcji jest zależny od tego, czy `SomeType` jest typem wartości lub typem referencyjnym. Jeśli jest to typ wartości, instrukcja tworzy tablicę 10 elementów, z których każdy ma typ `SomeType`. Jeśli `SomeType` jest typem referencyjnym instrukcji tworzy tablicę 10 elementów, z których każdy jest ustawiana na odwołanie o wartości null.  
  
 Aby uzyskać więcej informacji na temat typów wartości i typy referencyjne, zobacz [typów](../../../csharp/language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
