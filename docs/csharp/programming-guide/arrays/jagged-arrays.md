---
title: Tablice nieregularne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 2e4988439000712f4d1bd9b5abe412e7fd5d43eb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261673"
---
# <a name="jagged-arrays-c-programming-guide"></a>Tablice nieregularne (Przewodnik programowania w języku C#)

Nieregularna tablica to ta, której elementy są tablicami. Elementy tablicy nieregularnej może być inny wymiarów i rozmiarów. Nieregularna tablica jest czasami nazywane "tablicy tablic." W poniższych przykładach pokazano sposób deklarowania, zainicjować i dostępu nierówne tablic.  
  
 Deklaracja tablicy jednowymiarowej, która ma trzy elementy, w każdej z nich jest Jednowymiarowa tablica liczb całkowitych jest następująca:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Przed użyciem `jaggedArray`, jego elementów musi być zainicjowany. Można zainicjować elementy następująco:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Każdy z elementów to Jednowymiarowa tablica liczb całkowitych. Pierwszy element jest tablica liczb całkowitych, 5, drugą jest wartość tablicy liczb całkowitych 4, a trzecia będzie tablicy liczb całkowitych 2.  
  
 Istnieje również możliwość użycia inicjatorów do wypełniania elementów tablicy przy użyciu wartości, w którym to przypadku nie trzeba rozmiar tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Można również zainicjować tablicy po deklaracji w następujący sposób:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Można użyć następujących skrócone formy. Należy zauważyć, że nie można pominąć `new` operator od inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślne elementy:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.  
  
 Aby uzyskać dostęp tablicy poszczególnych elementów, takich jak te przykłady:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 Istnieje możliwość mieszać nieregularnej i tablice wielowymiarowe. Poniżej przedstawiono deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, która zawiera trzy elementy dwuwymiarową tablicę o różnych rozmiarach. Aby uzyskać więcej informacji na temat tablice dwuwymiarowe, zobacz [tablic wielowymiarowych](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Można uzyskać dostęp do poszczególnych elementów, przedstawione w tym przykładzie, który wyświetla wartość elementu `[1,0]` tablicy pierwszy (wartość `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 Metoda `Length` zwraca liczbę tablicami, zawarte w tablicy nieregularnej. Na przykład, przy założeniu, że zostały zadeklarowane poprzednią tablicę ten wiersz:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 Zwraca wartość 3.  
  
## <a name="example"></a>Przykład

 W tym przykładzie tworzy tablicę, której elementy są tablicami. Każdy z elementów tablicy ma inny rozmiar.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Array>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Tablice](../../../csharp/programming-guide/arrays/index.md)  
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
