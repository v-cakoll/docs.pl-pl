---
title: Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512732"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="3f229-102">Klauzula Handles wymaga zmiennej WithEvents zdefiniowanej w zawierającym ją typie lub jednym z jej typów podstawowych</span><span class="sxs-lookup"><span data-stu-id="3f229-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>
<span data-ttu-id="3f229-103">W klauzuli nie podano `WithEvents`zmiennej `Handles` .</span><span class="sxs-lookup"><span data-stu-id="3f229-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="3f229-104">Słowo kluczowe na końcu deklaracji procedury powoduje obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną `WithEvents` za pomocą słowa kluczowego. `Handles`</span><span class="sxs-lookup"><span data-stu-id="3f229-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>
  
 <span data-ttu-id="3f229-105">**Identyfikator błędu:** BC30506</span><span class="sxs-lookup"><span data-stu-id="3f229-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3f229-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="3f229-106">To correct this error</span></span>
  
- <span data-ttu-id="3f229-107">Podaj wymaganą `WithEvents` zmienną.</span><span class="sxs-lookup"><span data-stu-id="3f229-107">Supply the necessary `WithEvents` variable.</span></span>
  
## <a name="example"></a><span data-ttu-id="3f229-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f229-108">Example</span></span>

<span data-ttu-id="3f229-109">W poniższym przykładzie Visual Basic generuje błąd `BC30506` kompilatora, ponieważ słowo kluczowe [WithEvents](../modifiers/withevents.md) nie jest używane w definicji <xref:System.Timers.Timer?displayProperty=nameWithType> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3f229-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="3f229-110">Poniższy przykład kompiluje się pomyślnie, ponieważ `_timer1` zmienna jest zdefiniowana `WithEvents` za pomocą słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="3f229-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3f229-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f229-111">See also</span></span>

- [<span data-ttu-id="3f229-112">Handles</span><span class="sxs-lookup"><span data-stu-id="3f229-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
