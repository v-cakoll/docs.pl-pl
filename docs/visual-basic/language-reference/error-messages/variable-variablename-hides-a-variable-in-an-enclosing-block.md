---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 15c35cbb829bec782771b584ea25b111b81b5e1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766893"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Zmienna "\<nazwa_zmiennej >" ukrywa zmienną w otaczającym bloku
Zmienna ujęte w blok ma taką samą nazwę jak inny zmiennej lokalnej.  
  
 **Identyfikator błędu:** BC30616  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień nazwę zmiennej w bloku ujęty, tak aby nie była taka sama jak inne zmienne lokalne. Na przykład:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń. Jeśli jest to możliwe, nadaj nazwę `Catch` zmienna bloku `ex` zamiast `e`.  
  
- Wspólne źródło innego wystąpienia tego błędu jest próba dostępu zmienna lokalna zadeklarowana wewnątrz `Try` blok w osobnym `Catch` bloku. Aby rozwiązać ten problem, należy zadeklarować zmiennej poza `Try...Catch...Finally` struktury.  
  
## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
