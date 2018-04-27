---
title: Zdarzenia &#39; &lt;eventname1&gt; &#39; nie może implementować zdarzenia &#39; &lt;eventname2&gt; &#39; interfejsu &#39; &lt;interfejsu&gt; &#39; ponieważ ich typy delegowane &#39; &lt;delegate1&gt; &#39; i &#39; &lt;delegate2&gt; &#39; nie są zgodne
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Zdarzenia &#39; &lt;eventname1&gt; &#39; nie może implementować zdarzenia &#39; &lt;eventname2&gt; &#39; interfejsu &#39; &lt;interfejsu&gt; &#39; ponieważ ich typy delegowane &#39; &lt;delegate1&gt; &#39; i &#39; &lt;delegate2&gt; &#39; nie są zgodne
Visual Basic nie może implementować zdarzenia, ponieważ typ delegata zdarzenia nie pasuje do typu delegata zdarzenia w interfejsie. Ten błąd może wystąpić, gdy zdefiniować wiele zdarzeń w interfejsie, a następnie ponów próbę wykonania wraz z tego samego zdarzenia. Zdarzenia można zaimplementować dwa lub więcej zdarzeń tylko wtedy, gdy wszystko jest implementowane zdarzenia są zadeklarowane za pomocą `As` składni i określ ten sam typ delegata.  
  
 **Identyfikator błędu:** BC31423  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdarzenia należy wdrożyć osobno.  
  
     —lub—  
  
-   Definiowanie zdarzeń za pomocą interfejsu `As` składni i określ ten sam typ delegata.  
  
## <a name="see-also"></a>Zobacz też  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
