---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592064"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Zmienna "\<variablename >" ukrywa zmienną w otaczającym bloku
Zmienna ujęta w bloku ma taką samą nazwę jak inna zmienna lokalna.  
  
 **Identyfikator błędu:** BC30616  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień nazwę zmiennej w załączonym bloku, tak aby nie była taka sama jak jakakolwiek inna zmienna lokalna. Na przykład:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń. W takim przypadku należy nazwać zmienną bloku `Catch` `ex`, a nie `e`.  
  
- Innym wspólnym źródłem tego błędu jest próba uzyskania dostępu do zmiennej lokalnej zadeklarowanej w bloku `Try` w osobnym bloku `Catch`. Aby rozwiązać ten krok, należy zadeklarować zmienną poza strukturą `Try...Catch...Finally`.  
  
## <a name="see-also"></a>Zobacz także

- [Try...Catch...Finally, instrukcja](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
