---
title: 'Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2b8a35459fdeb7cce0b494a9b3024a79bd4173cc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic
*Zdarzeń* jest akcji lub wystąpienie — takie jak myszy przekroczony kliknij lub limit kredytu — który jest rozpoznawany przez inny składnik programu i dla którego można napisać kod do odpowiedzi. *Obsługi zdarzeń* jest zapisywany kod, aby odpowiadać na zdarzenie.  
  
 Program obsługi zdarzeń w języku Visual Basic jest `Sub` procedury. Jednak możesz nie zwykle wywołują go taki sam sposób jak inne `Sub` procedury. Zamiast tego należy zidentyfikować procedury obsługi dla zdarzenia. Można to zrobić za pomocą [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli i [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) zmiennej lub [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Przy użyciu `Handles` klauzula jest domyślną metodą Aby zadeklarować program obsługi zdarzeń w języku Visual Basic. Jest to sposób obsługi zdarzeń są zapisywane przez projektantów podczas programowania zintegrowane środowisko programistyczne (IDE). `AddHandler` Instrukcja jest odpowiedni dla wywoływanie zdarzeń dynamicznie w czasie wykonywania.  
  
 Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje procedurę obsługi zdarzenia. Wszelki kod, który ma dostęp do zdarzenia mogą spowodować on wystąpić, wykonując [RaiseEvent — instrukcja](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Z tego samego zdarzenia można skojarzyć więcej niż jeden program obsługi zdarzeń. W niektórych przypadkach można skojarzenie obsługi z zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Aby wywołać przy użyciu dojścia i WithEvents program obsługi zdarzeń  
  
1.  Upewnij się, że zdarzenie jest zadeklarowany za pomocą [Event — instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Deklarowanie zmiennej obiektu w module lub klasy poziomu przy użyciu [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) — słowo kluczowe. `As` Klauzula dla tej zmiennej musi określać klasy, która wywołuje zdarzenie.  
  
3.  W deklaracji obsługi zdarzeń `Sub` procedury dodawania [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli, która określa `WithEvents` zmienną i nazwa zdarzenia.  
  
4.  Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje `Sub` procedury. Można użyć kodu `RaiseEvent` oświadczenie wystąpić zdarzenie.  
  
     W poniższym przykładzie zdefiniowano zdarzenia i `WithEvents` zmiennej, która odwołuje się do klasy, która wywołuje zdarzenie. Obsługa zdarzeń `Sub` używa procedury `Handles` klauzuli, aby określić klasę i obsługi zdarzeń.  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Aby wywołać przy użyciu metody AddHandler program obsługi zdarzeń  
  
1.  Upewnij się, że zdarzenie jest zadeklarowany za pomocą `Event` instrukcji.  
  
2.  Wykonanie [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nawiązać dynamicznie obsługi zdarzeń `Sub` procedury ze zdarzeniem.  
  
3.  Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje `Sub` procedury. Można użyć kodu `RaiseEvent` oświadczenie wystąpić zdarzenie.  
  
     W poniższym przykładzie zdefiniowano `Sub` procedury obsługi <xref:System.Windows.Forms.Form.Closing> zdarzeń formularza. Następnie używa [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) do skojarzenia `catchClose` procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Usuń skojarzenie program obsługi zdarzeń z zdarzenie, wykonując [RemoveHandler — instrukcja](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub, procedury](./sub-procedures.md)  
 [Sub, instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [AddressOf, operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Instrukcje: tworzenie procedury](./how-to-create-a-procedure.md)  
 [Instrukcje: wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
