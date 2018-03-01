---
title: Oczekiwano inicjatora
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 46ff91ec240212571f7ec9f26e82d9d128263545
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Inicjatory obiektów: Typy nazwane i anonimowe](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Porady: deklarowanie obiektu za pomocą inicjatora obiektów](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
