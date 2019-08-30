---
title: Korzystanie z wariancji wC#delegatach ()
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 980caf8d5e4699115d203a89fab7994d18cc1707
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168361"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="7c708-102">Korzystanie z wariancji wC#delegatach ()</span><span class="sxs-lookup"><span data-stu-id="7c708-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="7c708-103">Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody.</span><span class="sxs-lookup"><span data-stu-id="7c708-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="7c708-104">Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze.</span><span class="sxs-lookup"><span data-stu-id="7c708-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="7c708-105">Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="7c708-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="7c708-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="7c708-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="7c708-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c708-107">Description</span></span>  
 <span data-ttu-id="7c708-108">Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="7c708-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="7c708-109">Typ danych zwracanych przez `DogsHandler` element jest typu `Dogs` `Mammals` , który pochodzi od typu, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="7c708-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7c708-110">Kod</span><span class="sxs-lookup"><span data-stu-id="7c708-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="7c708-111">Przykład 2: Kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="7c708-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="7c708-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7c708-112">Description</span></span>

<span data-ttu-id="7c708-113">W tym przykładzie pokazano, jak obiekty delegowane mogą być używane z metodami, które mają parametry, których typy są typami podstawowymi typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="7c708-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="7c708-114">Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="7c708-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="7c708-115">W poniższym przykładzie użyto dwóch delegatów:</span><span class="sxs-lookup"><span data-stu-id="7c708-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="7c708-116">Delegat definiujący podpis zdarzenia [Button. KeyDown.](xref:System.Windows.Forms.Control.KeyDown) <xref:System.Windows.Forms.KeyEventHandler></span><span class="sxs-lookup"><span data-stu-id="7c708-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="7c708-117">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="7c708-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="7c708-118">Delegat definiujący sygnaturę zdarzenia [Button. MouseClick.](xref:System.Windows.Forms.Control.MouseDown) <xref:System.Windows.Forms.MouseEventHandler></span><span class="sxs-lookup"><span data-stu-id="7c708-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="7c708-119">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="7c708-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="7c708-120">W przykładzie zdefiniowano procedurę obsługi zdarzeń z <xref:System.EventArgs> parametrem i używa jej do obsługi `Button.KeyDown` zarówno zdarzenia `Button.MouseClick` , jak i.</span><span class="sxs-lookup"><span data-stu-id="7c708-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="7c708-121">Można to zrobić, ponieważ <xref:System.EventArgs> jest typem podstawowym obu <xref:System.Windows.Forms.KeyEventArgs> i <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="7c708-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span> 
  
### <a name="code"></a><span data-ttu-id="7c708-122">Kod</span><span class="sxs-lookup"><span data-stu-id="7c708-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c708-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c708-123">See also</span></span>

- [<span data-ttu-id="7c708-124">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="7c708-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="7c708-125">Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()</span><span class="sxs-lookup"><span data-stu-id="7c708-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
