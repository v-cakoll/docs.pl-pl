---
title: Tablice jednowymiarowe — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: bd4ab53a9cb53e5cf636601bff5ac64a10a310a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170354"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>Tablice jednowymiarowe (Przewodnik programowania w języku C#)

Można zadeklarować jednowymiarową tablicę pięciu liczb całkowitych, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 Ta tablica zawiera `array[0]` `array[4]`elementy od do . [Nowy](../../language-reference/operators/new-operator.md) operator jest używany do tworzenia tablicy i inicjowania elementów tablicy do ich wartości domyślnych. W tym przykładzie wszystkie elementy tablicy są inicjowane do zera.  
  
 Tablica, która przechowuje elementy ciągu mogą być zadeklarowane w ten sam sposób. Przykład:  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy

 Istnieje możliwość zainicjowania tablicy na deklarację, w którym to przypadku specyfikator długości nie jest potrzebny, ponieważ jest już dostarczany przez liczbę elementów na liście inicjalizacji. Przykład:  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 Tablica ciągów może być inicjowana w ten sam sposób. Poniżej przedstawiono deklarację tablicy ciągów, w której każdy element tablicy jest inicjowany przez nazwę dnia:  

 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 Podczas inicjowania tablicy na deklarację, można użyć następujących skrótów:  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 Istnieje możliwość zadeklarowania zmiennej tablicy bez inicjowania, ale należy użyć `new` operatora podczas przypisywania tablicy do tej zmiennej. Przykład:  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 wprowadza niejawnie wpisane tablice. Aby uzyskać więcej informacji, zobacz [Tablice wpisane niejawnie](./implicitly-typed-arrays.md).  
  
## <a name="value-type-and-reference-type-arrays"></a>Tablice typów wartości i typów odwołań

 Należy wziąć pod uwagę następującą deklarację tablicy:  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 Wynik tej instrukcji zależy `SomeType` od tego, czy jest typem wartości, czy typem odwołania. Jeśli jest typem wartości, instrukcja tworzy tablicę 10 elementów, `SomeType`z których każdy ma typ . Jeśli `SomeType` jest typem odwołania, instrukcja tworzy tablicę 10 elementów, z których każdy jest inicjowany do odwołania null.  
  
Aby uzyskać więcej informacji na temat typów wartości i typów odwołań, zobacz [Typy wartości](../../language-reference/builtin-types/value-types.md) i [Typy odwołań](../../language-reference/keywords/reference-types.md).
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Array>
- [Przewodnik programowania języka C#](../index.md)
- [Tablice](./index.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
- [Tablice nieregularne](./jagged-arrays.md)
