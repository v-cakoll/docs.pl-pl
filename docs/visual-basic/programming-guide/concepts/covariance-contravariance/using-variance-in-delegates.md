---
title: Korzystanie z wariancji w Delegatach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 19eb3070c1b8359a4eb050e7cf2f16622f66ebe9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679798"
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="e02da-102">Korzystanie z wariancji w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e02da-102">Using Variance in Delegates (Visual Basic)</span></span>

<span data-ttu-id="e02da-103">Po przypisaniu metody z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typu delegata z podpis metody.</span><span class="sxs-lookup"><span data-stu-id="e02da-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="e02da-104">Kowariancja zezwala na metodę, aby zwracany typ, który jest bardziej pochodnego niż zdefiniowanymi dla delegata.</span><span class="sxs-lookup"><span data-stu-id="e02da-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="e02da-105">Kontrawariancja umożliwia metody, która ma typy parametrów, które są mniej pochodnego niż typ delegata.</span><span class="sxs-lookup"><span data-stu-id="e02da-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>

## <a name="example-1-covariance"></a><span data-ttu-id="e02da-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="e02da-106">Example 1: Covariance</span></span>

### <a name="description"></a><span data-ttu-id="e02da-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e02da-107">Description</span></span>

<span data-ttu-id="e02da-108">W tym przykładzie pokazano, jak można używać delegatów za pomocą metod, które mają zwracane typy, które są uzyskiwane ze zwracanego typu w podpisie delegata.</span><span class="sxs-lookup"><span data-stu-id="e02da-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="e02da-109">Typ danych zwracanych przez `DogsHandler` typu `Dogs`, która pochodzi od klasy `Mammals` typu, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="e02da-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>

### <a name="code"></a><span data-ttu-id="e02da-110">Kod</span><span class="sxs-lookup"><span data-stu-id="e02da-110">Code</span></span>

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

## <a name="example-2-contravariance"></a><span data-ttu-id="e02da-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="e02da-111">Example 2: Contravariance</span></span>

### <a name="description"></a><span data-ttu-id="e02da-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e02da-112">Description</span></span>

<span data-ttu-id="e02da-113">W tym przykładzie pokazano, jak można używać delegatów za pomocą metody, które mają parametry typu, które typy podstawowe typu parametru podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="e02da-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="e02da-114">Za pomocą kontrawariancja możesz użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="e02da-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="e02da-115">Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i korzystać z niego przy użyciu `Button.MouseClick` zdarzenia, które wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzenia, które wysyła `KeyEventArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="e02da-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>

### <a name="code"></a><span data-ttu-id="e02da-116">Kod</span><span class="sxs-lookup"><span data-stu-id="e02da-116">Code</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e02da-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e02da-117">See also</span></span>

- [<span data-ttu-id="e02da-118">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e02da-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="e02da-119">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e02da-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
