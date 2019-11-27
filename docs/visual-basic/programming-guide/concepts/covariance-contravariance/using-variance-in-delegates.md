---
title: Korzystanie z wariancji w delegatach
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349029"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="f3aa2-102">Korzystanie z wariancji w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3aa2-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="f3aa2-103">Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="f3aa2-104">Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="f3aa2-105">Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="f3aa2-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="f3aa2-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="f3aa2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f3aa2-107">Description</span></span>

<span data-ttu-id="f3aa2-108">Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="f3aa2-109">Typ danych zwracanych przez `DogsHandler` jest typu `Dogs`, który pochodzi od typu `Mammals`, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="f3aa2-110">Kod</span><span class="sxs-lookup"><span data-stu-id="f3aa2-110">Code</span></span>

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a><span data-ttu-id="f3aa2-111">Przykład 2: kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="f3aa2-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="f3aa2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f3aa2-112">Description</span></span>

<span data-ttu-id="f3aa2-113">W tym przykładzie pokazano, jak obiekty delegowane mogą być używane z metodami, które mają parametry, których typy są typami podstawowymi typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="f3aa2-114">Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="f3aa2-115">W poniższym przykładzie użyto dwóch delegatów:</span><span class="sxs-lookup"><span data-stu-id="f3aa2-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="f3aa2-116">Delegat <xref:System.Windows.Forms.KeyEventHandler>, który definiuje podpis zdarzenia [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) .</span><span class="sxs-lookup"><span data-stu-id="f3aa2-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="f3aa2-117">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="f3aa2-117">Its signature is:</span></span>

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- <span data-ttu-id="f3aa2-118">Delegat <xref:System.Windows.Forms.MouseEventHandler>, który definiuje sygnaturę zdarzenia [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) .</span><span class="sxs-lookup"><span data-stu-id="f3aa2-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="f3aa2-119">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="f3aa2-119">Its signature is:</span></span>

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

<span data-ttu-id="f3aa2-120">W przykładzie zdefiniowano procedurę obsługi zdarzeń z parametrem <xref:System.EventArgs> i używa jej do obsługi zdarzeń `Button.KeyDown` i `Button.MouseClick`.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="f3aa2-121">Można to zrobić, ponieważ <xref:System.EventArgs> jest typem podstawowym obu <xref:System.Windows.Forms.KeyEventArgs> i <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="f3aa2-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>

### <a name="code"></a><span data-ttu-id="f3aa2-122">Kod</span><span class="sxs-lookup"><span data-stu-id="f3aa2-122">Code</span></span>

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a><span data-ttu-id="f3aa2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3aa2-123">See also</span></span>

- [<span data-ttu-id="f3aa2-124">Wariancja w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3aa2-124">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="f3aa2-125">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3aa2-125">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
