---
title: 'Porady: sortowanie tablicy w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f24c0625058dbd960411d5981b4e98e0e9422b99
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Porady: sortowanie tablicy w Visual Basic
W tym przykładzie deklaruje tablicę `String` obiektów o nazwie `zooAnimals`, wypełnia go i następnie sortuje ją alfabetycznie.  
  
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
  
-   Dostęp do pliku Mscorlib.dll i <xref:System> przestrzeni nazw.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Tablica jest pusta (<xref:System.ArgumentNullException> klasy)  
  
-   Tablica jest wielowymiarowa (<xref:System.RankException> klasy)  
  
-   Co najmniej jeden element w tablicy nie implementują <xref:System.IComparable> interfejsu (<xref:System.InvalidOperationException> klasy)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Rozwiązywanie problemów związanych z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Kolekcje](../../concepts/collections.md)  
 [For Each...Next, instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
