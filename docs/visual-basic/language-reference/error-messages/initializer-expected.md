---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586389"
---
# <a name="initializer-expected"></a>Oczekiwano inicjatora
Nastąpiła próba Zadeklaruj wystąpienie klasy za pomocą inicjatora obiektów, w którym listy inicjowania jest pusta, jak pokazano w poniższym przykładzie.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Co najmniej jedno pole lub właściwość musi być zainicjowany na liście inicjatora, jak pokazano w poniższym przykładzie.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Identyfikator błędu:** BC30996  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Inicjowanie co najmniej jednego pola lub właściwości w inicjatorze, albo nie używaj inicjatora obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
