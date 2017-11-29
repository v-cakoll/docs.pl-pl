---
title: "Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0635e1b18b24a241fabad6d67da34f8dde9530db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym
A `For Each` pętli używa tablicy jako jego *elementu* zmiennej iteracji, ale inicjuje tablicy.  
  
 Poniższe instrukcje przedstawiają sposób tego błędu mogą być generowane.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 Pierwszy `For Each` instrukcja jest prawidłowy sposób do dostępu do elementów `arrayList`. Drugi `For Each` instrukcji generuje ten błąd.  
  
 **Identyfikator błędu:** BC32039  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń inicjowania z deklaracji *elementu* zmiennej iteracyjnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Dla... Next — instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Kolekcje](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
