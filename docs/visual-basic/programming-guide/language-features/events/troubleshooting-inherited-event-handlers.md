---
title: Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345106"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic
W tym temacie wymieniono typowe problemy związane z obsługą zdarzeń w składnikach dziedziczonych.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Kod w obsłudze zdarzeń jest wykonywany dwukrotnie dla każdego wywołania  
  
- Dziedziczona procedura obsługi zdarzeń nie może zawierać klauzuli [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) . Metoda w klasie bazowej jest już skojarzona ze zdarzeniem i zostanie odpowiednio wyzwolona. Usuń klauzulę `Handles` z dziedziczonej metody.  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- Jeśli dziedziczona Metoda nie ma słowa kluczowego `Handles`, należy sprawdzić, czy kod nie zawiera dodatkowej [instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ani żadnych dodatkowych metod, które obsługują to samo zdarzenie.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md)
