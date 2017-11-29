---
title: "Funkcja &#39; &lt;nazwaprocedury&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Funkcja &#39; &lt;nazwaprocedury&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
Funkcja "\<nazwaprocedury >' nie zwraca wartości we wszystkich ścieżkach kodu. Czy nie brakuje instrukcji "Return"?  
  
 A `Function` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który nie zwraca wartości.  
  
 Zostanie zwrócona wartość `Function` procedury w jednym z następujących sposobów:  
  
-   Włącz wartość w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Przypisuje wartość do `Function` procedury nazwę, a następnie wykonać `Exit Function` instrukcji.  
  
-   Przypisuje wartość do `Function` procedury nazwę, a następnie wykonać `End Function` instrukcji.  
  
 Jeśli formant przekazuje do `Exit Function` lub `End Function` i nie przypisano żadnej wartości na nazwę procedury, procedura zwraca wartość domyślna typu zwracanych danych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42105  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logika przepływu sterowania i upewnij się, że można przypisać wartości przed każdym instrukcji, która powoduje, że typ zwracany.  
  
     Ułatwia zagwarantować co zwrotu z procedury zwraca wartość, jeśli używasz zawsze `Return` instrukcji. Jeśli to zrobisz, ostatniej instrukcji przed `End Function` powinien być `Return` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury funkcji](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
