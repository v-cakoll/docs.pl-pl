---
title: Tablice nieregularne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="jagged-arrays-c-programming-guide"></a>Tablice nieregularne (Przewodnik programowania w języku C#)
Nieregularna tablica to ta, której elementy są tablicami. Elementy tablicy nieregularnej mogą być różne wymiary i rozmiary. Tablicy nieregularnej jest czasami nazywany "tablicy tablic." Poniższe przykłady pokazują, jak zadeklarować, zainicjować i tablice nieregularne dostępu.  
  
 Poniżej przedstawiono deklaracji jednowymiarowej tablicy, która ma trzy elementy, z których każdy jest tablicy jednowymiarowej liczb całkowitych:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Przed użyciem `jaggedArray`, jego elementy muszą zostać zainicjowane. Można zainicjować elementy następująco:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Każdy z elementów jest tablicy jednowymiarowej liczb całkowitych. Pierwszy element jest tablica liczb całkowitych 5, drugi jest tablica liczb całkowitych 4, a trzeci jest tablica liczb całkowitych 2.  
  
 Istnieje również możliwość użycia inicjatory umożliwia wypełnienie elementów tablicy wartości, w którym to przypadku nie trzeba rozmiar tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Można również zainicjować tablicy po deklaracji w następujący sposób:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Można użyć w następującej formie skrótu. Należy zauważyć, że nie można pominąć `new` operatora z inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślnych elementów:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Nieregularna tablica jest tablicy tablic, a w związku z tym jej elementy są typy referencyjne i są inicjowane na `null`.  
  
 Aby dostęp do tablicy poszczególnych elementów, takich jak te przykłady:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 Istnieje możliwość mieszać Tablice nieregularne i wielowymiarowych. Poniżej znajduje się deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, który zawiera trzy elementy tablicą dwuwymiarową o różnych rozmiarach. Aby uzyskać więcej informacji dotyczących dwuwymiarowa tablic, zobacz [tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Można uzyskać dostępu do poszczególne elementy, jak pokazano w przykładzie wyświetla wartość elementu `[1,0]` pierwszy tablicy (wartość `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 Metoda `Length` zwraca liczbę tablice zawartych w tablicy nieregularnej. Na przykład przy założeniu, że zadeklarowaniu poprzedniej macierzy, ten wiersz:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 Zwraca wartość 3.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kompilacje tablicy, której elementy są tablic. Każda z nich elementów tablicy ma inny rozmiar.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
