---
title: 'Porady: sortowanie tablicy w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: 467d1bcce6bda2feb5a8e59c152cb292d753e79b
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700973"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Instrukcje: sortowanie tablicy w Visual Basic

W tym artykule przedstawiono przykład sortowania tablicy ciągów w Visual Basic.

## <a name="example"></a>Przykład

Ten przykład deklaruje tablicę obiektów `String` o nazwie `zooAnimals`, wypełnia ją, a następnie sortuje ją alfabetycznie:
  
```vb
Private Sub SortAnimals()
    Dim zooAnimals(2) As String
    zooAnimals(0) = "lion"
    zooAnimals(1) = "turtle"
    zooAnimals(2) = "ostrich"
    Array.Sort(zooAnimals)
End Sub
```

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą spowodować wyjątek:

- Tablica jest pusta (Klasa <xref:System.ArgumentNullException>).
- Tablica jest wielowymiarowa (Klasa <xref:System.RankException>).
- Co najmniej jeden element tablicy nie implementuje interfejsu <xref:System.IComparable> (Klasa <xref:System.InvalidOperationException>).

## <a name="see-also"></a>Zobacz także

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- [Tablice](index.md)
- [Rozwiązywanie problemów związanych z tablicami](troubleshooting-arrays.md)
- [Kolekcje](../../concepts/collections.md)
- [For Each...Next, instrukcja](../../../language-reference/statements/for-each-next-statement.md)
