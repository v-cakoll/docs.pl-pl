---
title: Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 94c4229d4036382e344cffb09295e218642c55d4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402904"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="071c6-102">Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych</span><span class="sxs-lookup"><span data-stu-id="071c6-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>

<span data-ttu-id="071c6-103">W klauzuli nie podano `WithEvents` zmiennej `Handles` .</span><span class="sxs-lookup"><span data-stu-id="071c6-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="071c6-104">`Handles`Słowo kluczowe na końcu deklaracji procedury powoduje obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą `WithEvents` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="071c6-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>

<span data-ttu-id="071c6-105">**Identyfikator błędu:** BC30506</span><span class="sxs-lookup"><span data-stu-id="071c6-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="071c6-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="071c6-106">To correct this error</span></span>

<span data-ttu-id="071c6-107">Podaj wymaganą `WithEvents` zmienną.</span><span class="sxs-lookup"><span data-stu-id="071c6-107">Supply the necessary `WithEvents` variable.</span></span>

## <a name="example"></a><span data-ttu-id="071c6-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="071c6-108">Example</span></span>

<span data-ttu-id="071c6-109">W poniższym przykładzie Visual Basic generuje błąd kompilatora, `BC30506` ponieważ słowo kluczowe [WithEvents](../modifiers/withevents.md) nie jest używane w definicji <xref:System.Timers.Timer?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="071c6-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

<span data-ttu-id="071c6-110">Poniższy przykład kompiluje się pomyślnie, ponieważ `_timer1` zmienna jest zdefiniowana za pomocą `WithEvents` słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="071c6-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a><span data-ttu-id="071c6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="071c6-111">See also</span></span>

- [<span data-ttu-id="071c6-112">Handles</span><span class="sxs-lookup"><span data-stu-id="071c6-112">Handles</span></span>](../statements/handles-clause.md)
