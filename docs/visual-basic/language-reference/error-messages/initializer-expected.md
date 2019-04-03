---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 77cfeb57bc313ded2d2c4d5a0c59041c5c19f515
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826083"
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
