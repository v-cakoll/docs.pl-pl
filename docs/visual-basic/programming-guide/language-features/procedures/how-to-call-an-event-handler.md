---
title: 'Instrukcje: wywoływanie procedury obsługi zdarzeń'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 0c626a9ad92fe2cd0ea117a9abdd2965a09df2ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340426"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic

*Zdarzenie* jest akcją lub wystąpieniem, takim jak kliknięcie myszą lub Przekroczono limit środków, który jest rozpoznawany przez jakiś składnik programu i dla którego można napisać kod, aby odpowiedzieć. *Program obsługi zdarzeń* to kod, który można napisać, aby odpowiedzieć na zdarzenie.

 Procedura obsługi zdarzeń w Visual Basic jest procedurą `Sub`. Nie jest to jednak zazwyczaj wywoływana w taki sam sposób jak w przypadku innych procedur `Sub`. Zamiast tego należy zidentyfikować procedurę jako program obsługi zdarzenia. Można to zrobić z klauzulą [Handles](../../../language-reference/statements/handles-clause.md) i zmienną [WithEvents](../../../language-reference/modifiers/withevents.md) lub z [instrukcją AddHandler](../../../language-reference/statements/addhandler-statement.md). Użycie klauzuli `Handles` jest domyślnym sposobem deklarowania programu obsługi zdarzeń w Visual Basic. Jest to sposób, w jaki programy obsługi zdarzeń są zapisywane przez projektantów podczas programowania w zintegrowanym środowisku programistycznym (IDE). Instrukcja `AddHandler` jest odpowiednia do dynamicznego wywoływania zdarzeń w czasie wykonywania.

 Gdy wystąpi zdarzenie, Visual Basic automatycznie wywołuje procedurę obsługi zdarzeń. Każdy kod, który ma dostęp do zdarzenia może być spowodowany przez wykonanie [instrukcji RaiseEvent](../../../language-reference/statements/raiseevent-statement.md).

 Można skojarzyć więcej niż jeden program obsługi zdarzeń z tym samym zdarzeniem. W niektórych przypadkach można usunąć skojarzenie procedury obsługi ze zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Aby wywołać procedurę obsługi zdarzeń przy użyciu dojść i WithEvents

1. Upewnij się, że zdarzenie jest zadeklarowane za pomocą [instrukcji zdarzenia](../../../language-reference/statements/event-statement.md).

2. Zadeklaruj zmienną obiektu na poziomie modułu lub klasy przy użyciu słowa kluczowego [WithEvents](../../../language-reference/modifiers/withevents.md) . Klauzula `As` dla tej zmiennej musi określać klasę, która wywołuje zdarzenie.

3. W deklaracji procedury `Sub` obsługi zdarzeń Dodaj klauzulę [Handles](../../../language-reference/statements/handles-clause.md) , która określa zmienną `WithEvents` i nazwę zdarzenia.

4. Gdy wystąpi zdarzenie, Visual Basic automatycznie wywoła procedurę `Sub`. Kod może użyć instrukcji `RaiseEvent`, aby wystąpiło zdarzenie.

     W poniższym przykładzie zdefiniowano zdarzenie i zmienną `WithEvents`, która odwołuje się do klasy, która wywołuje zdarzenie. Procedura `Sub` obsługi zdarzeń używa klauzuli `Handles` do określenia klasy i zdarzenia, które obsługuje.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>Aby wywołać procedurę obsługi zdarzeń przy użyciu elementu AddHandler

1. Upewnij się, że zdarzenie jest zadeklarowane za pomocą instrukcji `Event`.

2. Wykonaj [instrukcję AddHandler](../../../language-reference/statements/addhandler-statement.md) , aby dynamicznie połączyć procedurę `Sub` obsługi zdarzeń ze zdarzeniem.

3. Gdy wystąpi zdarzenie, Visual Basic automatycznie wywoła procedurę `Sub`. Kod może użyć instrukcji `RaiseEvent`, aby wystąpiło zdarzenie.

     Poniższy przykład definiuje procedurę `Sub`, aby obsłużyć zdarzenie <xref:System.Windows.Forms.Form.Closing> formularza. Następnie używa [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md) do skojarzenia procedury `catchClose` jako procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     Można usunąć skojarzenie programu obsługi zdarzeń ze zdarzenia przez wykonanie [instrukcji RemoveHandler](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>Zobacz także

- [Procedury](index.md)
- [Sub, procedury](sub-procedures.md)
- [Sub, instrukcja](../../../language-reference/statements/sub-statement.md)
- [AddressOf, operator](../../../language-reference/operators/addressof-operator.md)
- [Instrukcje: tworzenie procedury](how-to-create-a-procedure.md)
- [Instrukcje: wywoływanie procedury, która nie zwraca wartości](how-to-call-a-procedure-that-does-not-return-a-value.md)
