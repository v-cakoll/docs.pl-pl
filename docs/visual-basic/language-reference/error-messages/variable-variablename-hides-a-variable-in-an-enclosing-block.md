---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 68ec1aac7ee8d292e2a433e0fb35039d4fb317b4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278502"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Zmienna "\<nazwa_zmiennej >" ukrywa zmienną w otaczającym bloku
Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.  
  
 **Identyfikator błędu:** BC30616  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień nazwę zmiennej w bloku ujęty, tak aby nie była taka sama jak inne zmienne lokalne. Na przykład:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń. Jeśli jest to możliwe, nadaj nazwę `Catch` zmienna bloku `ex` zamiast `e`.  
  
-   Wspólne źródło innego wystąpienia tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w osobnym `Catch` bloku. Aby rozwiązać ten problem, należy zadeklarować zmiennej poza `Try...Catch...Finally` struktury.  
  
## <a name="see-also"></a>Zobacz także
- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
