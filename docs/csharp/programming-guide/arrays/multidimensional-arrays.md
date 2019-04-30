---
title: Tablice wielowymiarowe - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683928"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Tablice wielowymiarowe (Przewodnik programowania w języku C#)

Tablice mogą mieć więcej niż jeden wymiar. Na przykład następująca deklaracja tworzy dwuwymiarową tablicę cztery wiersze i dwie kolumny.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Następująca deklaracja tworzy tablicę o trzech wymiarów, 4, 2 i 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Inicjowanie tablicy

 Można zainicjować tablicy po zgłoszeniu, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Możesz również zainicjować tablicy bez określania rangi.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Jeśli zdecydujesz się zadeklarować zmiennej tablicy bez inicjowania, należy użyć `new` operatora, aby przypisać tablicę do zmiennej. Korzystanie z `new` przedstawiono w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Poniższy przykład przypisuje wartość do elementu określonej tablicy.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Podobnie poniższy przykład pobiera wartość elementu określonego tablicy i przypisuje go do zmiennej `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Poniższy przykład kodu inicjuje elementy tablicy, do wartości domyślnych (z wyjątkiem tablic nieregularnych).  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Tablice](../../../csharp/programming-guide/arrays/index.md)
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Tablice nieregularne](../../../csharp/programming-guide/arrays/jagged-arrays.md)
