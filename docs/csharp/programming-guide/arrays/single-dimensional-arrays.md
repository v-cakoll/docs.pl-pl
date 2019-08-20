---
title: Tablice jednowymiarowe — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 17c384ec327d4a80ed614dce6254baa5bfb2e960
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597313"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tablice jednowymiarowe (Przewodnik programowania w języku C#)

Można zadeklarować jednowymiarową tablicę składającą się z pięciu liczb całkowitych, jak pokazano w następującym przykładzie:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Ta tablica zawiera elementy z `array[0]` elementu do. `array[4]` Operator [New](../../language-reference/operators/new-operator.md) jest używany do tworzenia tablicy i inicjowania elementów tablicy do ich wartości domyślnych. W tym przykładzie wszystkie elementy tablicy są inicjowane do zera.  
  
 Tablica, która przechowuje elementy ciągu, może być zadeklarowana w ten sam sposób. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy

 Możliwe jest zainicjowanie tablicy przy użyciu deklaracji, w takim przypadku specyfikator długości nie jest wymagany, ponieważ jest już dostarczany przez liczbę elementów na liście inicjalizacji. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Tablicę ciągów można zainicjować w taki sam sposób. Poniżej znajduje się deklaracja tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Po zainicjowaniu tablicy po zgłoszeniu można użyć następujących skrótów:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Istnieje możliwość zadeklarować zmienną tablicową bez inicjalizacji, ale należy użyć `new` operatora, gdy przypiszesz tablicę do tej zmiennej. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C#3,0 wprowadza niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [niejawnie wpisane tablice](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Typ wartości i tablice typów referencyjnych

 Rozważmy następującą deklarację tablicy:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Wynik tej instrukcji zależy od tego, czy `SomeType` jest typem wartości czy typem referencyjnym. Jeśli jest to typ wartości, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy ma typ `SomeType`. Jeśli `SomeType` jest typem referencyjnym, instrukcja tworzy tablicę zawierającą 10 elementów, z których każdy jest zainicjowany do odwołania o wartości null.  
  
 Aby uzyskać więcej informacji na temat typów wartości i typów referencyjnych, zobacz [Types](../../language-reference/keywords/types.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
