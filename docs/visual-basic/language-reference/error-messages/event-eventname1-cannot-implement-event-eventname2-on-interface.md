---
title: Zdarzenie „<eventname1>” nie może implementować zdarzenia „<eventname2>” w interfejsie „<interface>”, ponieważ ich typy delegowane „<delegate1>” i „<delegate2>” są niezgodne
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 9581168fa86f8f0715e004b60c2eb2a813cd38ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803305"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Zdarzenie "\<eventname1 >' nie może implementować zdarzenia"\<eventname2 > "w interfejsie"\<interfejsu > "ponieważ ich typy delegowane\<delegate1 >" i "\<delegate2 >' nie są zgodne
Visual Basic nie może implementować zdarzenia, ponieważ typ delegata zdarzenia jest niezgodny z typem delegata, zdarzenia w interfejsie. Ten błąd może wystąpić, gdy można zdefiniować wiele zdarzeń w interfejsie, a następnie spróbuj ich implementacji wraz z tego samego zdarzenia. Zdarzenie można zaimplementować dwa lub więcej zdarzeń tylko wtedy, gdy wszystko jest implementowane zdarzenia są deklarowane przy użyciu `As` składni i określić ten sam typ delegata.  
  
 **Identyfikator błędu:** BC31423  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zdarzenia należy wdrożyć osobno.  
  
     —lub—  
  
- Definiowanie zdarzenia przy użyciu interfejsu `As` składni i określić ten sam typ delegata.  
  
## <a name="see-also"></a>Zobacz także

- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
