---
title: Nierówne tablic - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 026132b99821c01e6b7a6c02ee571ae3144319c3
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971822"
---
# <a name="jagged-arrays-c-programming-guide"></a>Tablice nieregularne (Przewodnik programowania w języku C#)

Nieregularna tablica to ta, której elementy są tablicami. Elementy tablicy nieregularnej może być inny wymiarów i rozmiarów. Nieregularna tablica jest czasami nazywane "tablicy tablic." W poniższych przykładach pokazano sposób deklarowania, zainicjować i dostępu nierówne tablic.  
  
 Deklaracja tablicy jednowymiarowej, która ma trzy elementy, w każdej z nich jest Jednowymiarowa tablica liczb całkowitych jest następująca:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Przed użyciem `jaggedArray`, jego elementów musi być zainicjowany. Można zainicjować elementy następująco:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Każdy z elementów to Jednowymiarowa tablica liczb całkowitych. Pierwszy element jest tablica liczb całkowitych, 5, drugą jest wartość tablicy liczb całkowitych 4, a trzecia będzie tablicy liczb całkowitych 2.  
  
 Istnieje również możliwość użycia inicjatorów do wypełniania elementów tablicy przy użyciu wartości, w którym to przypadku nie trzeba rozmiar tablicy. Na przykład:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Można również zainicjować tablicy po deklaracji w następujący sposób:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Można użyć następujących skrócone formy. Należy zauważyć, że nie można pominąć `new` operator od inicjowania elementów ponieważ nie istnieje żadne inicjowanie domyślne elementy:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Nieregularna tablica jest tablicy tablic, a zatem jej elementy są typami odwołań i są inicjowane na `null`.  
  
 Aby uzyskać dostęp tablicy poszczególnych elementów, takich jak te przykłady:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Istnieje możliwość mieszać nieregularnej i tablice wielowymiarowe. Poniżej przedstawiono deklaracji i inicjowania jednowymiarowej tablicy nieregularnej, która zawiera trzy elementy dwuwymiarową tablicę o różnych rozmiarach. Aby uzyskać więcej informacji na temat tablice dwuwymiarowe, zobacz [tablic wielowymiarowych](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Można uzyskać dostęp do poszczególnych elementów, przedstawione w tym przykładzie, który wyświetla wartość elementu `[1,0]` tablicy pierwszy (wartość `5`):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Metoda `Length` zwraca liczbę tablicami, zawarte w tablicy nieregularnej. Na przykład, przy założeniu, że zostały zadeklarowane poprzednią tablicę ten wiersz:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 Zwraca wartość 3.  
  
## <a name="example"></a>Przykład

 W tym przykładzie tworzy tablicę, której elementy są tablicami. Każdy z elementów tablicy ma inny rozmiar.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Array>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Tablice](../../../csharp/programming-guide/arrays/index.md)
- [Tablice jednowymiarowe](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [Tablice wielowymiarowe](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
