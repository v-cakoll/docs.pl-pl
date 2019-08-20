---
title: Tablice nieregularne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 8d1be351e3aabea44138323d04c922dd1cccb78a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597327"
---
# <a name="jagged-arrays-c-programming-guide"></a>Tablice nieregularne (Przewodnik programowania w języku C#)

Nieregularna tablica to ta, której elementy są tablicami. Elementy tablicy nieregularnej mogą mieć różne wymiary i rozmiary. Tablica nieregularna jest czasami nazywana "tablicą tablic." W poniższych przykładach pokazano, jak deklarować, inicjować i uzyskiwać dostęp do tablic nieregularnych.  
  
 Poniżej znajduje się deklaracja jednowymiarowej tablicy, która składa się z trzech elementów, z których każdy jest jednowymiarową tablicą liczb całkowitych:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Zanim będzie można użyć `jaggedArray`, jego elementy muszą zostać zainicjowane. Można inicjować następujące elementy:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Każdy element jest jednowymiarową tablicą liczb całkowitych. Pierwszy element jest tablicą 5 liczb całkowitych, a druga jest tablicą 4 liczb całkowitych, a trzecia jest tablicą 2 liczb całkowitych.  
  
 Istnieje również możliwość użycia inicjatorów do wypełnienia elementów tablicy wartościami, w tym przypadku nie jest potrzebny rozmiar tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Możesz również zainicjować tablicę w przypadku deklaracji takich jak:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Możesz użyć następującej formy skróconej. Należy zauważyć, że nie można `new` pominąć operatora z inicjowania elementów, ponieważ nie ma domyślnego inicjowania dla elementów:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Tablica nieregularna jest tablicą tablic, dlatego jej elementy są typami odwołań i są inicjowane do `null`.  
  
 Można uzyskać dostęp do poszczególnych elementów tablicy, takich jak następujące przykłady:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Możliwe jest mieszanie tablic nieregularnych i wielowymiarowych. Poniżej znajduje się deklaracja i Inicjalizacja jednowymiarowej tablicy nieregularnej, która zawiera 3 2-wymiarowe elementy tablicy o różnych rozmiarach. Aby uzyskać więcej informacji na temat tablic dwuwymiarowych, zobacz [wielowymiarowe tablice](./multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Można uzyskać dostęp do poszczególnych elementów, jak pokazano w tym przykładzie, który wyświetla wartość elementu `[1,0]` pierwszej tablicy (wartość `5`):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Metoda `Length` zwraca liczbę tablic zawartych w tablicy nieregularnej. Na przykład przy założeniu, że zadeklarowano poprzednią tablicę, ten wiersz:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 Zwraca wartość 3.  
  
## <a name="example"></a>Przykład

 Ten przykład kompiluje tablicę, której elementy same są tablicami. Każdy jeden z elementów tablicy ma inny rozmiar.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Przewodnik programowania w języku C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
