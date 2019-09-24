---
title: 'Instrukcje: Wywołaj procedurę obsługi zdarzeń w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216616"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Instrukcje: Wywołaj procedurę obsługi zdarzeń w Visual Basic

*Zdarzenie* jest akcją lub wystąpieniem, takim jak kliknięcie myszą lub Przekroczono limit środków, który jest rozpoznawany przez jakiś składnik programu i dla którego można napisać kod, aby odpowiedzieć. *Program obsługi zdarzeń* to kod, który można napisać, aby odpowiedzieć na zdarzenie.

 `Sub` Procedura obsługi zdarzeń w Visual Basic jest procedurą. Nie jest to jednak zazwyczaj wywoływana w taki sam sposób jak w przypadku `Sub` innych procedur. Zamiast tego należy zidentyfikować procedurę jako program obsługi zdarzenia. Można to zrobić z klauzulą [Handles](../../../language-reference/statements/handles-clause.md) i zmienną [WithEvents](../../../language-reference/modifiers/withevents.md) lub z [instrukcją AddHandler](../../../language-reference/statements/addhandler-statement.md). `Handles` Użycie klauzuli jest domyślnym sposobem deklarowania procedury obsługi zdarzeń w Visual Basic. Jest to sposób, w jaki programy obsługi zdarzeń są zapisywane przez projektantów podczas programowania w zintegrowanym środowisku programistycznym (IDE). `AddHandler` Instrukcja jest odpowiednia do dynamicznego wywoływania zdarzeń w czasie wykonywania.

 Gdy wystąpi zdarzenie, Visual Basic automatycznie wywołuje procedurę obsługi zdarzeń. Każdy kod, który ma dostęp do zdarzenia może być spowodowany przez wykonanie [instrukcji RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Można skojarzyć więcej niż jeden program obsługi zdarzeń z tym samym zdarzeniem. W niektórych przypadkach można usunąć skojarzenie procedury obsługi ze zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Aby wywołać procedurę obsługi zdarzeń przy użyciu dojść i WithEvents

1. Upewnij się, że zdarzenie jest zadeklarowane za pomocą [instrukcji zdarzenia](../../../language-reference/statements/event-statement.md).

2. Zadeklaruj zmienną obiektu na poziomie modułu lub klasy przy użyciu słowa kluczowego [WithEvents](../../../language-reference/modifiers/withevents.md) . `As` Klauzula dla tej zmiennej musi określać klasę, która wywołuje zdarzenie.

3. W deklaracji procedury obsługi `Sub` zdarzeń Dodaj `WithEvents` klauzulę [Handles](../../../language-reference/statements/handles-clause.md) , która określa zmienną i nazwę zdarzenia.

4. Gdy wystąpi zdarzenie, Visual Basic automatycznie wywoła `Sub` procedurę. Kod może użyć `RaiseEvent` instrukcji, aby wystąpiło zdarzenie.

     W poniższym przykładzie zdefiniowano zdarzenie i `WithEvents` zmienną, która odwołuje się do klasy, która wywołuje zdarzenie. Procedura obsługi `Sub` zdarzeń `Handles` używa klauzuli do określenia klasy i zdarzenia, które obsługuje.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Aby wywołać procedurę obsługi zdarzeń przy użyciu elementu AddHandler

1. Upewnij się, że zdarzenie jest zadeklarowane `Event` za pomocą instrukcji.

2. Wykonaj [instrukcję AddHandler](../../../language-reference/statements/addhandler-statement.md) , aby dynamicznie połączyć procedurę obsługi `Sub` zdarzeń ze zdarzeniem.

3. Gdy wystąpi zdarzenie, Visual Basic automatycznie wywoła `Sub` procedurę. Kod może użyć `RaiseEvent` instrukcji, aby wystąpiło zdarzenie.

     W poniższym przykładzie zdefiniowano `Sub` procedurę <xref:System.Windows.Forms.Form.Closing> obsługi zdarzenia formularza. Następnie używa [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md) , aby skojarzyć `catchClose` procedurę jako procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Można usunąć skojarzenie programu obsługi zdarzeń ze zdarzenia przez wykonanie [instrukcji RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Zobacz także

- [Procedury](index.md)
- [Sub, procedury](sub-procedures.md)
- [Sub, instrukcja](../../../language-reference/statements/sub-statement.md)
- [AddressOf, operator](../../../language-reference/operators/addressof-operator.md)
- [Instrukcje: Tworzenie procedury](how-to-create-a-procedure.md)
- [Instrukcje: Wywoływanie procedury, która nie zwraca wartości](how-to-call-a-procedure-that-does-not-return-a-value.md)
