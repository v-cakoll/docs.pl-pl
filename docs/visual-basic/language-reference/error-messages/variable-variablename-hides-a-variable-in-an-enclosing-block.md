---
title: Zmienna &#39; &lt;nazwa_zmiennej&gt; &#39; ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595095"
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Zmienna &#39; &lt;nazwa_zmiennej&gt; &#39; ukrywa zmienną w otaczającym bloku
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
 [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
