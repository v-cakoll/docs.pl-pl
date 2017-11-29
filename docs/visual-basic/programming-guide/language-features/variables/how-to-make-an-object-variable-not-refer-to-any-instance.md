---
title: "Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)
Usuń skojarzenie zmienna obiektu z dowolnego wystąpienia obiektu przez ustawienie jej na [nic](../../../../visual-basic/language-reference/nothing.md).  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>Aby usunąć skojarzenie z dowolnego wystąpienia obiektu zmienna obiektu  
  
-   Ustaw zmienną na `Nothing` w instrukcji przypisania.  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Jeśli kod spróbuje uzyskiwanie dostępu do członka zmiennej obiektu, który został ustawiony na `Nothing`, <xref:System.NullReferenceException> występuje. Jeśli ustawiono zmienną obiektu `Nothing` często, czy jest możliwe, zmienna nie jest zainicjowany, jest dobrze jest umieścić uzyskuje dostęp do elementu członkowskiego w `Try...Catch...Finally` bloku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli użyjesz zmiennej obiektu dla obiektów, które zawierają dane poufne lub można ustawić zmiennej `Nothing` po ma się nie aktywnie do czynienia z jedną z tych obiektów. Zmniejsza ryzyko złośliwy kod, aby uzyskać dostęp do danych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.NullReferenceException>  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try... CATCH... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Rozwiązywanie problemów z wyjątkami: System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
