---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 1fa66a3c50b5c1eadd4c63b92c57ab60e1a11076
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595997"
---
# <a name="initializer-expected"></a>Oczekiwano inicjatora
Próbowano deklarować wystąpienia klasy za pomocą inicjatora obiektów, w którym listy inicjowania jest pusta, jak pokazano w poniższym przykładzie.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Co najmniej jedno pole lub właściwość musi być zainicjowany na liście inicjatora, jak pokazano w poniższym przykładzie.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Identyfikator błędu:** BC30996  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Inicjowanie co najmniej jednego pola lub właściwości w inicjatorze lub nie należy używać inicjatora obiektów.  
  
## <a name="see-also"></a>Zobacz także
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
