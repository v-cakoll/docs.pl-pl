---
title: Korzystanie z wariancji wC#delegatach ()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 00e11d4ce755c8c75b73023fec14d95ebc96b4fe
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595261"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="8a465-102">Korzystanie z wariancji wC#delegatach ()</span><span class="sxs-lookup"><span data-stu-id="8a465-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="8a465-103">Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody.</span><span class="sxs-lookup"><span data-stu-id="8a465-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="8a465-104">Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze.</span><span class="sxs-lookup"><span data-stu-id="8a465-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="8a465-105">Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="8a465-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="8a465-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="8a465-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a465-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8a465-107">Description</span></span>  
 <span data-ttu-id="8a465-108">Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="8a465-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="8a465-109">Typ danych zwracanych przez `DogsHandler` element jest typu `Dogs` `Mammals` , który pochodzi od typu, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="8a465-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a465-110">Kod</span><span class="sxs-lookup"><span data-stu-id="8a465-110">Code</span></span>  
  
```csharp  
class Mammals {}  
class Dogs : Mammals {}  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="8a465-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="8a465-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="8a465-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8a465-112">Description</span></span>  
 <span data-ttu-id="8a465-113">W tym przykładzie pokazano, jak można używać delegatów z metodami, które mają parametry typu, które są typami podstawowymi typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="8a465-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="8a465-114">Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="8a465-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="8a465-115">Można na przykład utworzyć procedurę obsługi zdarzeń, `EventArgs` która akceptuje parametr wejściowy, i użyć go `Button.MouseClick` ze zdarzeniem, które wysyła `MouseEventArgs` typ `TextBox.KeyDown` jako parametr, `KeyEventArgs` a także ze zdarzeniem, które wysyła parametr.</span><span class="sxs-lookup"><span data-stu-id="8a465-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a465-116">Kod</span><span class="sxs-lookup"><span data-stu-id="8a465-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a465-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a465-117">See also</span></span>

- [<span data-ttu-id="8a465-118">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="8a465-118">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="8a465-119">Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()</span><span class="sxs-lookup"><span data-stu-id="8a465-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
