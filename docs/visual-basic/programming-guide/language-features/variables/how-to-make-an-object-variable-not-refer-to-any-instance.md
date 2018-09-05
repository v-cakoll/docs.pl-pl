---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 8f85ba0adea522851e45b20ef5024491874c9a29
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564531"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)
Usuń skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu przez ustawienie [nic](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Aby usunąć skojarzenie z dowolnego wystąpienia obiektu zmiennej obiektu  
  
-   Ustaw zmienną na `Nothing` w instrukcji przypisania.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli kod próbuje uzyskać dostępu do członka zmienną obiektu, który został ustawiony na `Nothing`, <xref:System.NullReferenceException> występuje. Jeśli zmienna obiektu jest ustawiona na `Nothing` często, lub jeśli jest to możliwe, zmienna nie została zainicjowana, to dobry pomysł, aby ująć dostępie do elementów członkowskich w `Try...Catch...Finally` bloku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Użycie zmiennej obiektu dla obiektów, które zawierają dane poufne, można ustawić zmiennej `Nothing` kiedy masz nie aktywnie do czynienia z jedną z tych obiektów. Zmniejsza to prawdopodobieństwo złośliwego kodu, uzyskiwanie dostępu do danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.NullReferenceException>  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Rozwiązywanie problemów z wyjątkami: System.NullReferenceException](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
