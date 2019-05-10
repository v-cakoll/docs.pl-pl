---
title: Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym
ms.date: 07/20/2015
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords:
- BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
ms.openlocfilehash: 9f24dd2a20dc3a4935cd288a20a0e12c1d47bee1
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912345"
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a>Tablica zadeklarowana jako zmienna sterująca pętli for nie może być zadeklarowana z rozmiarem początkowym
A `For Each` pętli używa tablicy jako jego *elementu* Zmienna iteracji, ale inicjuje tej tablicy.  
  
 Poniższe instrukcje przedstawiają, jak ten błąd może zostać wygenerowany.  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 Pierwszy `For Each` instrukcja jest poprawny sposób dostępu do elementów `arrayList`. Drugi `For Each` instrukcja generuje ten błąd.  
  
 **Identyfikator błędu:** BC32039  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń inicjowania z deklaracji *elementu* Zmienna iteracji.  
  
## <a name="see-also"></a>Zobacz także

- [For...Next, instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Tablice](../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Kolekcje](../../../standard/collections/index.md)
