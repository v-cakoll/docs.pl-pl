---
title: Korzystanie z wariancji w Delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 44a6153a9a1c0aa0aebb18710ea9e770fd4e57fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668968"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="8ddb0-102">Korzystanie z wariancji w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="8ddb0-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="8ddb0-103">Po przypisaniu metody z delegatem, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dopasowanie typu delegata z podpis metody.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="8ddb0-104">Kowariancja zezwala na metodę, aby zwracany typ, który jest bardziej pochodnego niż zdefiniowanymi dla delegata.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="8ddb0-105">Kontrawariancja umożliwia metody, która ma typy parametrów, które są mniej pochodnego niż typ delegata.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="8ddb0-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="8ddb0-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="8ddb0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ddb0-107">Description</span></span>  
 <span data-ttu-id="8ddb0-108">W tym przykładzie pokazano, jak można używać delegatów za pomocą metod, które mają zwracane typy, które są uzyskiwane ze zwracanego typu w podpisie delegata.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="8ddb0-109">Typ danych zwracanych przez `DogsHandler` typu `Dogs`, która pochodzi od klasy `Mammals` typu, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8ddb0-110">Kod</span><span class="sxs-lookup"><span data-stu-id="8ddb0-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="8ddb0-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="8ddb0-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="8ddb0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8ddb0-112">Description</span></span>  
 <span data-ttu-id="8ddb0-113">W tym przykładzie pokazano, jak można używać delegatów za pomocą metody, które mają parametry typu, które typy podstawowe typu parametru podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="8ddb0-114">Za pomocą kontrawariancja możesz użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="8ddb0-115">Na przykład można utworzyć program obsługi zdarzeń, który akceptuje `EventArgs` parametr wejściowy i korzystać z niego przy użyciu `Button.MouseClick` zdarzenia, które wysyła `MouseEventArgs` typu jako parametru, a także z `TextBox.KeyDown` zdarzenia, które wysyła `KeyEventArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="8ddb0-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8ddb0-116">Kod</span><span class="sxs-lookup"><span data-stu-id="8ddb0-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ddb0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ddb0-117">See also</span></span>

- [<span data-ttu-id="8ddb0-118">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="8ddb0-118">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [<span data-ttu-id="8ddb0-119">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="8ddb0-119">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
