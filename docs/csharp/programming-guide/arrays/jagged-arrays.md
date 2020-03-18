---
title: Postrzępione tablice — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705707"
---
# <a name="jagged-arrays-c-programming-guide"></a>Tablice nieregularne (Przewodnik programowania w języku C#)

Nieregularna tablica to ta, której elementy są tablicami. Elementy postrzępionej tablicy mogą mieć różne wymiary i rozmiary. Postrzępiona tablica jest czasami nazywana "tablicą tablic". W poniższych przykładach przedstawiono sposób deklarowania, inicjowania i uzyskiwania dostępu do tablic postrzępionych.  
  
 Poniżej przedstawiono deklarację tablicy jednowymiarowej, która ma trzy elementy, z których każdy jest jednowymiarową tablicą liczb całkowitych:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Przed użyciem, `jaggedArray`jego elementy muszą zostać zainicjowane. Można zainicjować elementy w ten sposób:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Każdy z elementów jest jednowymiarową tablicą liczb całkowitych. Pierwszy element jest tablicą 5 liczb całkowitych, drugi jest tablicą 4 liczb całkowitych, a trzeci jest tablicą 2 liczb całkowitych.  
  
 Możliwe jest również użycie inicjatorów do wypełnienia elementów tablicy wartościami, w którym to przypadku nie jest potrzebny rozmiar tablicy. Przykład:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Tablicę można również zainicjować przy deklaracji w ten sposób:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Można użyć następującego skróconego formularza. Należy zauważyć, że `new` nie można pominąć operatora z inicjowania elementów, ponieważ nie ma domyślnej inicjalizacji dla elementów:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Postrzępiona tablica jest tablicą tablic i dlatego jej elementy `null`są typami odwołań i są inicjowane do .  
  
 Można uzyskać dostęp do poszczególnych elementów tablicy, takich jak te przykłady:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Możliwe jest mieszanie postrzępionych i wielowymiarowych tablic. Poniżej przedstawiono deklarację i inicjowanie jednowymiarowej tablicy postrzępionej, która zawiera trzy dwuwymiarowe elementy tablicy o różnych rozmiarach. Aby uzyskać więcej informacji na temat tablic dwuwymiarowych, zobacz [Tablice wielowymiarowe](./multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Można uzyskać dostęp do poszczególnych elementów, jak pokazano `[1,0]` w tym przykładzie, `5`który wyświetla wartość elementu pierwszej tablicy (wartość):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Metoda `Length` zwraca liczbę tablic zawartych w tablicy postrzępionej. Na przykład przy założeniu, że zadeklarowano poprzednią tablicę, ten wiersz:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 zwraca wartość 3.  
  
## <a name="example"></a>Przykład

 W tym przykładzie tworzy tablicy, których elementy są same tablice. Każdy z elementów tablicy ma inny rozmiar.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Array>
- [Przewodnik programowania języka C#](../index.md)
- [Tablice](./index.md)
- [Tablice jednowymiarowe](./single-dimensional-arrays.md)
- [Tablice wielowymiarowe](./multidimensional-arrays.md)
