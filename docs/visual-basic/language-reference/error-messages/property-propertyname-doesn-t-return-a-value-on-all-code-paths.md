---
title: "Właściwości &#39; &lt;propertyname&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Właściwości &#39; &lt;propertyname&gt;&#39; &#39;t zwraca wartości we wszystkich ścieżkach kodu
Właściwość "\<propertyname >' nie zwraca wartości we wszystkich ścieżkach kodu. W czasie wykonywania, gdy zostanie użyty wynik może wystąpić wyjątek odwołania zerowego.  
  
 Właściwość `Get` procedura ma co najmniej jedną ścieżkę możliwe za pośrednictwem jego kod, który nie zwraca wartości.  
  
 Może zwracać wartości z właściwości `Get` procedury w jednym z następujących sposobów:  
  
-   Przypisuje wartość do nazwy właściwości, a następnie wykonaj `Exit Property` instrukcji.  
  
-   Przypisuje wartość do nazwy właściwości, a następnie wykonaj `End Get` instrukcji.  
  
-   Włącz wartość w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Jeśli formant przekazuje do `Exit Property` lub `End Get` i nie przypisano żadnej wartości do nazwy właściwości `Get` procedury zwraca wartość domyślna właściwości typu danych. Aby uzyskać więcej informacji, zobacz "Zachowanie" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42107  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Sprawdź logika przepływu sterowania i upewnij się, że można przypisać wartości przed każdym instrukcji, która powoduje, że typ zwracany.  
  
     Ułatwia zagwarantować co zwrotu z procedury zwraca wartość, jeśli używasz zawsze `Return` instrukcji. Jeśli to zrobisz, ostatniej instrukcji przed `End Get` powinien być `Return` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury własności](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get — instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)
