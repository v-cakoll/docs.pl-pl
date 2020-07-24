---
title: Korzystanie z wariancji w delegatach (C#)
description: Dowiedz się, jak używać wariancji w delegatach przy użyciu dołączonych przykładów kodu Kowariancja i kontrawariancja.
ms.date: 07/20/2015
ms.assetid: 1638c95d-dc8b-40c1-972c-c2dcf84be55e
ms.openlocfilehash: 62b0555ee29c5e7d2ba0954a8949d61596122cc7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105685"
---
# <a name="using-variance-in-delegates-c"></a><span data-ttu-id="ed726-103">Korzystanie z wariancji w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="ed726-103">Using Variance in Delegates (C#)</span></span>
<span data-ttu-id="ed726-104">Podczas przypisywania metody do delegata, *Kowariancja* i *kontrawariancja* zapewniają elastyczność dla dopasowania typu delegata z sygnaturą metody.</span><span class="sxs-lookup"><span data-stu-id="ed726-104">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="ed726-105">Kowariancja zezwala metodzie na typ zwracany, który jest bardziej pochodny niż zdefiniowany w delegatze.</span><span class="sxs-lookup"><span data-stu-id="ed726-105">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="ed726-106">Kontrawariancja zezwala na metodę, która ma typy parametrów, które są mniej pochodne niż te w typie delegata.</span><span class="sxs-lookup"><span data-stu-id="ed726-106">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="ed726-107">Przykład 1: Kowariancja</span><span class="sxs-lookup"><span data-stu-id="ed726-107">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed726-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ed726-108">Description</span></span>  
 <span data-ttu-id="ed726-109">Ten przykład pokazuje, jak obiekty delegowane mogą być używane z metodami, które mają typy zwracane, które pochodzą z typu zwracanego w sygnaturze delegata.</span><span class="sxs-lookup"><span data-stu-id="ed726-109">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="ed726-110">Typ danych zwracanych przez element `DogsHandler` jest typu `Dogs` , który pochodzi od `Mammals` typu, który jest zdefiniowany w delegacie.</span><span class="sxs-lookup"><span data-stu-id="ed726-110">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ed726-111">Kod</span><span class="sxs-lookup"><span data-stu-id="ed726-111">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="ed726-112">Przykład 2: kontrawariancja</span><span class="sxs-lookup"><span data-stu-id="ed726-112">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="ed726-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ed726-113">Description</span></span>

<span data-ttu-id="ed726-114">W tym przykładzie pokazano, jak obiekty delegowane mogą być używane z metodami, które mają parametry, których typy są typami podstawowymi typu parametru podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="ed726-114">This example demonstrates how delegates can be used with methods that have parameters whose types are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="ed726-115">Za pomocą kontrawariancja można użyć jednego programu obsługi zdarzeń zamiast oddzielnych programów obsługi.</span><span class="sxs-lookup"><span data-stu-id="ed726-115">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="ed726-116">W poniższym przykładzie użyto dwóch delegatów:</span><span class="sxs-lookup"><span data-stu-id="ed726-116">The following example makes use of two delegates:</span></span>

- <span data-ttu-id="ed726-117"><xref:System.Windows.Forms.KeyEventHandler>Delegat definiujący podpis zdarzenia [Button. KeyDown](xref:System.Windows.Forms.Control.KeyDown) .</span><span class="sxs-lookup"><span data-stu-id="ed726-117">A <xref:System.Windows.Forms.KeyEventHandler> delegate that defines the signature of the [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown) event.</span></span> <span data-ttu-id="ed726-118">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="ed726-118">Its signature is:</span></span>

   ```csharp
   public delegate void KeyEventHandler(object sender, KeyEventArgs e)
   ```

- <span data-ttu-id="ed726-119"><xref:System.Windows.Forms.MouseEventHandler>Delegat definiujący sygnaturę zdarzenia [Button. MouseClick](xref:System.Windows.Forms.Control.MouseDown) .</span><span class="sxs-lookup"><span data-stu-id="ed726-119">A <xref:System.Windows.Forms.MouseEventHandler> delegate that defines the signature of the [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown) event.</span></span> <span data-ttu-id="ed726-120">Podpis jest:</span><span class="sxs-lookup"><span data-stu-id="ed726-120">Its signature is:</span></span>

   ```csharp
   public delegate void MouseEventHandler(object sender, MouseEventArgs e)
   ```

<span data-ttu-id="ed726-121">W przykładzie zdefiniowano procedurę obsługi zdarzeń z <xref:System.EventArgs> parametrem i używa jej do obsługi zarówno `Button.KeyDown` zdarzenia, jak i `Button.MouseClick` .</span><span class="sxs-lookup"><span data-stu-id="ed726-121">The example defines an event handler with an <xref:System.EventArgs> parameter and uses it to handle both the `Button.KeyDown` and `Button.MouseClick` events.</span></span> <span data-ttu-id="ed726-122">Można to zrobić, ponieważ <xref:System.EventArgs> jest typem podstawowym obu <xref:System.Windows.Forms.KeyEventArgs> i <xref:System.Windows.Forms.MouseEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="ed726-122">It can do this because <xref:System.EventArgs> is a base type of both <xref:System.Windows.Forms.KeyEventArgs>  and <xref:System.Windows.Forms.MouseEventArgs>.</span></span>
  
### <a name="code"></a><span data-ttu-id="ed726-123">Kod</span><span class="sxs-lookup"><span data-stu-id="ed726-123">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ed726-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed726-124">See also</span></span>

- [<span data-ttu-id="ed726-125">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="ed726-125">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
- [<span data-ttu-id="ed726-126">Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)</span><span class="sxs-lookup"><span data-stu-id="ed726-126">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
