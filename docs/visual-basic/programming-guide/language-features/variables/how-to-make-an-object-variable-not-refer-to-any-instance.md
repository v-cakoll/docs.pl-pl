---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: e647f2f891b06aa1767faac49b01df98ea31ec1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004915"
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
 Jeśli kod próbuje uzyskać dostęp do elementu członkowskiego zmiennej obiektu, która została ustawiona na `Nothing`, występuje <xref:System.NullReferenceException>. Jeśli ustawisz zmienną obiektu na `Nothing` często, lub jeśli jest to możliwe, zmienna nie jest zainicjowana, dobrym pomysłem jest zablokowanie dostępu do składowych w bloku `Try...Catch...Finally`.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli używasz zmiennej obiektu dla obiektów, które zawierają dane poufne lub poufne, możesz ustawić zmienną `Nothing`, gdy nie będziesz aktywnie korzystać z jednego z tych obiektów. Zmniejsza to prawdopodobieństwo złośliwego kodu, który uzyskuje dostęp do danych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.NullReferenceException>
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
