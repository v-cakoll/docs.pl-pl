---
title: 'Instrukcje: Wywoływanie programu do obsługi zdarzeń w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3690d1c2eb8ece9059b8b25b5a14bef2021bc8f6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320174"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Instrukcje: Wywoływanie programu do obsługi zdarzeń w języku Visual Basic
*Zdarzeń* jest akcja lub zdarzenie — takich jak myszy kliknij lub limit środków przekroczyła — który jest rozpoznawany przez inny składnik programu i dla którego można napisać kod odpowiedzi. *Programu obsługi zdarzeń* znajduje się kod pisany w celu reagowania na zdarzenie.  
  
 Program obsługi zdarzeń w języku Visual Basic jest `Sub` procedury. Jednak nie zwykle wywołuje on taki sam sposób jak inne `Sub` procedur. Zamiast tego należy zidentyfikować procedury jako program obsługi zdarzenia. Można to zrobić za pomocą [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli i [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) zmiennej, lub za pomocą [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Za pomocą `Handles` klauzula jest domyślną metodą do deklarowania program obsługi zdarzeń w języku Visual Basic. Jest to sposób, w jaki procedury obsługi zdarzeń są zapisywane przez projektantów, gdy programujesz w zintegrowanym środowisku programistycznym (IDE). `AddHandler` Instrukcji jest odpowiednia dla podnoszonego zdarzenia dynamicznie w czasie wykonywania.  
  
 Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje procedurę obsługi zdarzenia. Wszelki kod, który ma dostęp do zdarzenia może spowodować, że występują, wykonując [RaiseEvent — instrukcja](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Z tego samego zdarzenia można skojarzyć więcej niż jeden program obsługi zdarzeń. W niektórych przypadkach można usunąć skojarzenia obsługi ze zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Aby wywołać procedurę obsługi zdarzeń za pomocą dojścia i WithEvents  
  
1. Upewnij się, że zdarzenie jest zadeklarowana za pomocą [Event — instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2. Deklarowanie zmiennej obiektu modułu lub klasy przy użyciu poziomu [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) — słowo kluczowe. `As` Klauzula dla tej zmiennej, należy określić klasę, która wywołuje zdarzenie.  
  
3. W deklaracji obsługi zdarzeń `Sub` procedury dodawania [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzula, która określa `WithEvents` zmienną i nazwa zdarzenia.  
  
4. Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje `Sub` procedury. Kod może użyć `RaiseEvent` instrukcję, aby utworzyć zdarzenia występują.  
  
     W poniższym przykładzie zdefiniowano zdarzenia i `WithEvents` zmiennej, która odwołuje się do klasy, która wywołuje zdarzenia. Obsługa zdarzeń `Sub` używa procedury `Handles` klauzuli, aby określić klasy i obsługi zdarzeń.  
  
     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>Aby wywołać procedurę obsługi zdarzeń za pomocą AddHandler  
  
1. Upewnij się, że zdarzenie jest zadeklarowana za pomocą `Event` instrukcji.  
  
2. Wykonaj [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) dynamicznie połączyć obsługi zdarzeń `Sub` procedury ze zdarzeniem.  
  
3. Po wystąpieniu zdarzenia, Visual Basic automatycznie wywołuje `Sub` procedury. Kod może użyć `RaiseEvent` instrukcję, aby utworzyć zdarzenia występują.  
  
     W poniższym przykładzie zdefiniowano `Sub` procedury, aby obsłużyć <xref:System.Windows.Forms.Form.Closing> zdarzeń formularza. Następnie używa [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) skojarzyć `catchClose` procedury jako program obsługi zdarzeń dla <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]  
  
     Usuń skojarzenie program obsługi zdarzenia ze zdarzenia, wykonując [RemoveHandler — instrukcja](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Zobacz także

- [Procedury](./index.md)
- [Sub, procedury](./sub-procedures.md)
- [Sub — Instrukcja](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Operator AddressOf](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrukcje: Tworzenie procedury](./how-to-create-a-procedure.md)
- [Instrukcje: Wywoływanie procedury, która nie zwraca wartości](./how-to-call-a-procedure-that-does-not-return-a-value.md)
