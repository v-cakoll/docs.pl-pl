---
title: 'Instrukcje: Sortowanie tablicy w języku Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 0b04bfbedf9d7266d1b2e190fa85b8a64cf6efbf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558439"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Instrukcje: Sortowanie tablicy w języku Visual Basic
Ten przykład deklaruje tablicę `String` obiektów o nazwie `zooAnimals`, wypełnia ją i następnie sortuje ją alfabetycznie.  
  
## <a name="example"></a>Przykład  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Dostęp do biblioteki Mscorlib.dll i <xref:System> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Tablica jest pusta (<xref:System.ArgumentNullException> klasy)  
  
-   Tablica ma charakter wielowymiarowy (<xref:System.RankException> klasy)  
  
-   Nie należy implementować jeden lub więcej elementów tablicy <xref:System.IComparable> interfejsu (<xref:System.InvalidOperationException> klasy)  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
- [Kolekcje](../../concepts/collections.md)
- [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
