---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352895"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)
Można usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu, ustawiając dla niego wartość [Nothing](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Aby usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu  
  
- Ustaw zmienną na `Nothing` w instrukcji przypisania.  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli kod próbuje uzyskać dostęp do elementu członkowskiego zmiennej obiektu, która została ustawiona na `Nothing`, wystąpi <xref:System.NullReferenceException>. Jeśli ustawisz zmienną obiektu na `Nothing` często lub jeśli jest możliwe, że zmienna nie została zainicjowana, dobrym pomysłem będzie zawrzeć dostęp do elementów członkowskich w bloku `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli używasz zmiennej obiektu dla obiektów, które zawierają dane poufne lub poufne, możesz ustawić zmienną do `Nothing`, gdy nie będziesz aktywnie korzystać z jednego z tych obiektów. Zmniejsza to prawdopodobieństwo złośliwego kodu, który uzyskuje dostęp do danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.NullReferenceException>
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
