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
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Rozwiązywanie problemów z tablicami](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Kolekcje](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [For Each... Next — instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
