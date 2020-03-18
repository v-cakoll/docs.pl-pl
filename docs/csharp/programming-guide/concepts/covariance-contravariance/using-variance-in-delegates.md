---
title: Używanie wariancji w delegatach (C#)
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 83e86e760edb17f6d9ae61864c154062d41416e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169769"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="4de2a-102">Używanie wariancji w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="4de2a-102">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="4de2a-103">Po przypisaniu metody do delegata, *kowariancja* i *contravariance* zapewniają elastyczność dopasowania typu delegata z podpisem metody.</span><span class="sxs-lookup"><span data-stu-id="4de2a-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="4de2a-104">Kowariancja pozwala metody mieć zwracany typ, który jest bardziej pochodną niż zdefiniowane w delegata.</span><span class="sxs-lookup"><span data-stu-id="4de2a-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="4de2a-105">Contravariance zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="4de2a-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="4de2a-106">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="4de2a-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="4de2a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4de2a-107">Description</span></span>  
 <span data-ttu-id="4de2a-108">W tym przykładzie pokazano, jak delegatów mogą być używane z metod, które mają typy zwracane, które są uzyskiwane z typu zwracanego w podpisie delegata.</span><span class="sxs-lookup"><span data-stu-id="4de2a-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="4de2a-109">Typ danych zwracany `DogsHandler` przez `Dogs`jest typu , `Mammals` który pochodzi od typu, który jest zdefiniowany w pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="4de2a-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4de2a-110">Code</span><span class="sxs-lookup"><span data-stu-id="4de2a-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="4de2a-111">Przykład 2: Contravariance</span><span class="sxs-lookup"><span data-stu-id="4de2a-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="4de2a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4de2a-112">Description</span></span>

<span data-ttu-id="4de2a-113">W tym przykładzie pokazano, jak delegatów mogą być używane z metod, które mają parametry, których typy są typy podstawowe typu typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="4de2a-113">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="4de2a-114">Z contravariance, można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="4de2a-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="4de2a-115">W poniższym przykładzie korzysta z dwóch delegatów:</span><span class="sxs-lookup"><span data-stu-id="4de2a-115">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="4de2a-116">Pełnomocnik, <xref:System.Windows.Forms.KeyEventHandler> który definiuje podpis [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4de2a-116">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="4de2a-117">Jego podpis jest:</span><span class="sxs-lookup"><span data-stu-id="4de2a-117">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="4de2a-118">Pełnomocnik <xref:System.Windows.Forms.MouseEventHandler> definiujący podpis zdarzenia [Button.MouseClick.](xref:System.Windows.Forms.Control.MouseDown)</span><span class="sxs-lookup"><span data-stu-id="4de2a-118">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="4de2a-119">Jego podpis jest:</span><span class="sxs-lookup"><span data-stu-id="4de2a-119">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="4de2a-120">W przykładzie definiuje program obsługi <xref:System.EventArgs> zdarzeń z parametrem `Button.KeyDown` `Button.MouseClick` i używa go do obsługi zarówno i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4de2a-120">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="4de2a-121">Można to zrobić, ponieważ <xref:System.EventArgs> jest <xref:System.Windows.Forms.KeyEventArgs> typem bazowym obu i <xref:System.Windows.Forms.MouseEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="4de2a-121">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="4de2a-122">Code</span><span class="sxs-lookup"><span data-stu-id="4de2a-122">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4de2a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4de2a-123">See also</span></span>

- [<span data-ttu-id="4de2a-124">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="4de2a-124">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="4de2a-125">Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)</span><span class="sxs-lookup"><span data-stu-id="4de2a-125">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
