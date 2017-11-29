---
title: Korzystanie z wariancji w Delegatach (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb8512945fa7aefa9afce4f4f1f8e0200dc3e2b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="f972a-102">Korzystanie z wariancji w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="f972a-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="f972a-103">Po przypisaniu metodę z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typem obiektu delegowanego przy użyciu podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="f972a-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="f972a-104">Kowariancja pozwala metoda ma typ zwracany jest bardziej pochodny niż zdefiniowana w elemencie delegowanym.</span><span class="sxs-lookup"><span data-stu-id="f972a-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="f972a-105">Kontrawariancja zezwala na metodę, która zawiera typy parametrów, które są mniej pochodnego od tych w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="f972a-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="f972a-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="f972a-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="f972a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f972a-107">Description</span></span>  
 <span data-ttu-id="f972a-108">W tym przykładzie pokazano, delegatów możliwości korzystania z metody, które mają zwracanych typów pochodzących z zwracany typ w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="f972a-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="f972a-109">Typ danych zwracanych przez `DogsHandler` jest typu `Dogs`, która jest pochodną `Mammals` typu, który jest zdefiniowany w elemencie delegowanym.</span><span class="sxs-lookup"><span data-stu-id="f972a-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f972a-110">Kod</span><span class="sxs-lookup"><span data-stu-id="f972a-110">Code</span></span>  
  
```csharp  
class Mammals{}  
class Dogs : Mammals{}  
  
class Program  
{  
    // Define the delegate.  
    public delegate Mammals HandlerMethod();  
  
    public static Mammals MammalsHandler()  
    {  
        return null;  
    }  
  
    public static Dogs DogsHandler()  
    {  
        return null;  
    }  
  
    static void Test()  
    {  
        HandlerMethod handlerMammals = MammalsHandler;  
  
        // Covariance enables this assignment.  
        HandlerMethod handlerDogs = DogsHandler;  
    }  
}  
```  
  
## <a name="example-2-contravariance"></a><span data-ttu-id="f972a-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="f972a-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="f972a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f972a-112">Description</span></span>  
 <span data-ttu-id="f972a-113">W przykładzie pokazano, jak delegatów można użyć z metod, które ma parametry typu, które typy podstawowe typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="f972a-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="f972a-114">Z kontrawariancji można użyć jednej procedury obsługi zdarzeń, zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="f972a-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="f972a-115">Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i używać go z `Button.MouseClick` zdarzeń, która wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzeń, która wysyła `KeyEventArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="f972a-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f972a-116">Kod</span><span class="sxs-lookup"><span data-stu-id="f972a-116">Code</span></span>  
  
```csharp  
// Event handler that accepts a parameter of the EventArgs type.  
private void MultiHandler(object sender, System.EventArgs e)  
{  
    label1.Text = System.DateTime.Now.ToString();  
}  
  
public Form1()  
{  
    InitializeComponent();  
  
    // You can use a method that has an EventArgs parameter,  
    // although the event expects the KeyEventArgs parameter.  
    this.button1.KeyDown += this.MultiHandler;  
  
    // You can use the same method   
    // for an event that expects the MouseEventArgs parameter.  
    this.button1.MouseClick += this.MultiHandler;  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f972a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f972a-117">See Also</span></span>  
 [<span data-ttu-id="f972a-118">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="f972a-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="f972a-119">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)</span><span class="sxs-lookup"><span data-stu-id="f972a-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
