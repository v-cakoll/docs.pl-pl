---
title: Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 52107589c6bbebbd34ecbb090845f4031612c276
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578934"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="ddf41-102">Wyrażenie lambda nie zostanie usunięte z tej obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="ddf41-102">Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="ddf41-103">Wyrażenie lambda nie zostanie usunięte z tej procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ddf41-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="ddf41-104">Przypisz wyrażenie lambda do zmiennej i Użyj zmiennej, aby dodać i usunąć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ddf41-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="ddf41-105">Gdy wyrażenia lambda są używane z obsługą zdarzeń, może nie być widoczne oczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ddf41-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="ddf41-106">Kompilator generuje nową metodę dla każdej definicji wyrażenia lambda, nawet jeśli są identyczne.</span><span class="sxs-lookup"><span data-stu-id="ddf41-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="ddf41-107">W związku z tym Poniższy kod wyświetla `False`.</span><span class="sxs-lookup"><span data-stu-id="ddf41-107">Therefore, the following code displays `False`.</span></span>

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

<span data-ttu-id="ddf41-108">Gdy wyrażenia lambda są używane z obsługą zdarzeń, może to spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="ddf41-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="ddf41-109">W poniższym przykładzie wyrażenie lambda dodane przez `AddHandler` nie jest usuwane przez instrukcję `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="ddf41-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

<span data-ttu-id="ddf41-110">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="ddf41-110">By default, this message is a warning.</span></span> <span data-ttu-id="ddf41-111">Aby uzyskać więcej informacji na temat sposobu ukrywania ostrzeżeń lub traktowania ostrzeżeń jako błędów, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ddf41-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="ddf41-112">**Identyfikator błędu:** BC42326</span><span class="sxs-lookup"><span data-stu-id="ddf41-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ddf41-113">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ddf41-113">To correct this error</span></span>

<span data-ttu-id="ddf41-114">Aby uniknąć ostrzeżenia i usunąć wyrażenie lambda, przypisz wyrażenie lambda do zmiennej i Użyj zmiennej w instrukcji `AddHandler` i `RemoveHandler`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ddf41-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="ddf41-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddf41-115">See also</span></span>

- [<span data-ttu-id="ddf41-116">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="ddf41-116">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="ddf41-117">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="ddf41-117">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="ddf41-118">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ddf41-118">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
