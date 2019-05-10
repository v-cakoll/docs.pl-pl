---
title: Zdarzenie „<eventname1>” nie może implementować zdarzenia „<eventname2>” w interfejsie „<interface>”, ponieważ ich typy delegowane „<delegate1>” i „<delegate2>” są niezgodne
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d6b85124b4408df532623f7c14a76e936ea28572
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625543"
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
