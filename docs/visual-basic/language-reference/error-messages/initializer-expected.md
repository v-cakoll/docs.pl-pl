---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402840"
---
# <a name="initializer-expected"></a>Oczekiwano inicjatora
Podjęto próbę zadeklarować wystąpienie klasy za pomocą inicjatora obiektu, w którym lista inicjalizacji jest pusta, jak pokazano w poniższym przykładzie.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Na liście inicjatorów musi być zainicjowana co najmniej jedno pole lub właściwość, jak pokazano w poniższym przykładzie.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **Identyfikator błędu:** BC30996  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Zainicjuj co najmniej jedno pole lub właściwość w inicjatorze lub nie używaj inicjatora obiektów.  
  
## <a name="see-also"></a>Zobacz też

- [Inicjatory obiektów: typy nazwane i anonimowe](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
