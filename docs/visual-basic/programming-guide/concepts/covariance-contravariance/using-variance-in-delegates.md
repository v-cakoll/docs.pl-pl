---
title: Korzystanie z wariancji w Delegatach (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 435591d69e67c4fc4be8e781c5f63e025c71a8cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="5403c-102">Korzystanie z wariancji w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5403c-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="5403c-103">Po przypisaniu metodę z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typem obiektu delegowanego przy użyciu podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="5403c-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="5403c-104">Kowariancja pozwala metoda ma typ zwracany jest bardziej pochodny niż zdefiniowana w elemencie delegowanym.</span><span class="sxs-lookup"><span data-stu-id="5403c-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="5403c-105">Kontrawariancja zezwala na metodę, która zawiera typy parametrów, które są mniej pochodnego od tych w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="5403c-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="5403c-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="5403c-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="5403c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5403c-107">Description</span></span>  
 <span data-ttu-id="5403c-108">W tym przykładzie pokazano, delegatów możliwości korzystania z metody, które mają zwracanych typów pochodzących z zwracany typ w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="5403c-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="5403c-109">Typ danych zwracanych przez `DogsHandler` jest typu `Dogs`, która jest pochodną `Mammals` typu, który jest zdefiniowany w elemencie delegowanym.</span><span class="sxs-lookup"><span data-stu-id="5403c-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5403c-110">Kod</span><span class="sxs-lookup"><span data-stu-id="5403c-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="5403c-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="5403c-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="5403c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5403c-112">Description</span></span>  
 <span data-ttu-id="5403c-113">W przykładzie pokazano, jak delegatów można użyć z metod, które ma parametry typu, które typy podstawowe typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="5403c-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="5403c-114">Z kontrawariancji można użyć jednej procedury obsługi zdarzeń, zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="5403c-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="5403c-115">Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i używać go z `Button.MouseClick` zdarzeń, która wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzeń, która wysyła `KeyEventArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="5403c-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5403c-116">Kod</span><span class="sxs-lookup"><span data-stu-id="5403c-116">Code</span></span>  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
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
  
## <a name="see-also"></a><span data-ttu-id="5403c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5403c-117">See Also</span></span>  
 [<span data-ttu-id="5403c-118">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5403c-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="5403c-119">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5403c-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
