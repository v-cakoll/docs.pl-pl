---
title: "Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; jest używana, zanim została do niej przypisana wartość"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Zmienna &#39; &lt;nazwa_zmiennej&gt;&#39; jest używana, zanim została do niej przypisana wartość
Zmienna "\<nazwa_zmiennej >" jest używana, zanim została do niej przypisana wartość. W czasie wykonywania może wystąpić wyjątek odwołania zerowego.  
  
 Aplikacja ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod odczytujący zmiennej przed przypisaniem do niej żadnej wartości.  
  
 Jeśli zmienna nie zostanie przypisana wartość, zawiera wartość domyślną dla tego typu danych. Odwołanie do typu danych, że wartość domyślna to [nic](../../../visual-basic/language-reference/nothing.md). Odczytywanie odwołanie do zmiennej, która ma wartość `Nothing` może spowodować <xref:System.NullReferenceException> w pewnych okolicznościach.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42104  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logika przepływu sterowania i upewnij się, że zmienna ma prawidłową wartość, zanim formant przekazuje do żadnych instrukcji, która odczytuje go.  
  
-   Jest jednym ze sposobów gwarantuje, że zmienna zawsze ma prawidłową wartość zainicjować go jako części swojej deklaracji. Zobacz sekcję "Inicjowanie" w [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Deklaracja zmiennej](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Rozwiązywanie problemów z zmiennych](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
