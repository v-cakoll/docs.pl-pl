---
title: Zdarzenie &#39; &lt;eventname1&gt; &#39; nie może implementować zdarzenia &#39; &lt;eventname2&gt; &#39; interfejsu &#39; &lt;interfejsu&gt; &#39; ponieważ ich typy delegowane &#39; &lt;delegate1&gt; &#39; i &#39; &lt;delegate2&gt; &#39; nie są zgodne
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638216"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Zdarzenie &#39; &lt;eventname1&gt; &#39; nie może implementować zdarzenia &#39; &lt;eventname2&gt; &#39; interfejsu &#39; &lt;interfejsu&gt; &#39; ponieważ ich typy delegowane &#39; &lt;delegate1&gt; &#39; i &#39; &lt;delegate2&gt; &#39; nie są zgodne
Visual Basic nie może implementować zdarzenia, ponieważ typ delegata zdarzenia jest niezgodny z typem delegata, zdarzenia w interfejsie. Ten błąd może wystąpić, gdy można zdefiniować wiele zdarzeń w interfejsie, a następnie spróbuj ich implementacji wraz z tego samego zdarzenia. Zdarzenie można zaimplementować dwa lub więcej zdarzeń tylko wtedy, gdy wszystko jest implementowane zdarzenia są deklarowane przy użyciu `As` składni i określić ten sam typ delegata.  
  
 **Identyfikator błędu:** BC31423  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdarzenia należy wdrożyć osobno.  
  
     —lub—  
  
-   Definiowanie zdarzenia przy użyciu interfejsu `As` składni i określić ten sam typ delegata.  
  
## <a name="see-also"></a>Zobacz także
- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
