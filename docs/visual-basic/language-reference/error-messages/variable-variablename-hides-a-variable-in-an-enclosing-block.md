---
title: "Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; ukrywa zmienną w otaczającym bloku"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2af570cd002b4be4e15a7c03b0ffc2ff84ba3982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; ukrywa zmienną w otaczającym bloku
Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.  
  
 **Identyfikator błędu:** BC30616  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień nazwę zmiennej w bloku objętego tak, aby nie jest taka sama jak innych zmiennych lokalnych. Na przykład:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz obsługi zdarzeń. Jeśli jest to możliwe, nazwę `Catch` zmienna bloku `ex` zamiast `e`.  
  
-   Inne typowe źródło tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w oddzielnej `Catch` bloku. Aby rozwiązać ten problem, należy zadeklarować zmienną poza `Try...Catch...Finally` struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Try... CATCH... Finally — instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
