---
title: Jak publikować zdarzenia zgodne z wytycznymi programu .NET Framework — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167540"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="d3b9f-102">Jak publikować zdarzenia zgodne z wytycznymi programu .NET Framework (Przewodnik programowania c#)</span><span class="sxs-lookup"><span data-stu-id="d3b9f-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="d3b9f-103">W poniższej procedurze przedstawiono sposób dodawania zdarzeń, które postępują zgodnie ze standardowym wzorcem .NET Framework do klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="d3b9f-104">Wszystkie zdarzenia w bibliotece klas .NET <xref:System.EventHandler> Framework są oparte na pełnomocniku, który jest zdefiniowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d3b9f-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="d3b9f-105">.NET Framework 2.0 wprowadza ogólną wersję tego <xref:System.EventHandler%601>delegata.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="d3b9f-106">W poniższych przykładach przedstawiono sposób używania obu wersji.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="d3b9f-107">Mimo że zdarzenia w klasach, które można zdefiniować może być oparta na dowolny prawidłowy typ delegata, nawet delegatów, <xref:System.EventHandler>które zwracają wartość, ogólnie zaleca się, aby oprzeć zdarzenia na wzorcu .NET Framework przy użyciu , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="d3b9f-108">Aby opublikować zdarzenia na podstawie wzorca EventHandler</span><span class="sxs-lookup"><span data-stu-id="d3b9f-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="d3b9f-109">(Pomiń ten krok i przejdź do kroku 3a, jeśli nie musisz wysyłać niestandardowych danych ze zdarzeniem). Zadeklarować klasę dla danych niestandardowych w zakresie, który jest widoczny zarówno dla wydawcy i klasy subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="d3b9f-110">Następnie dodaj wymaganych członków do przechowywania danych zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="d3b9f-111">W tym przykładzie zwracany jest prosty ciąg.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }
    }  
    ```  
  
2. <span data-ttu-id="d3b9f-112">(Pomiń ten krok, jeśli <xref:System.EventHandler%601> używasz ogólnej wersji .) Deklaruj pełnomocnika w klasie publikowania.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="d3b9f-113">Nadaj mu nazwę, która kończy się *eventhandler*.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="d3b9f-114">Drugi parametr określa niestandardowy typ EventArgs.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="d3b9f-115">Zadeklaruj zdarzenie w klasie publikowania, wykonując jedną z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="d3b9f-116">Jeśli nie masz niestandardowej klasy EventArgs, typ zdarzenia będzie nierodzajowym delegatem EventHandler.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="d3b9f-117">Nie trzeba zadeklarować delegata, ponieważ jest już <xref:System> zadeklarowany w obszarze nazw, który jest uwzględniony podczas tworzenia projektu C#.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="d3b9f-118">Dodaj następujący kod do klasy wydawcy.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="d3b9f-119">Jeśli używasz wersji nierodzajowej <xref:System.EventHandler> i masz klasę niestandardową <xref:System.EventArgs>wywodzącą się z , zadeklarować zdarzenie wewnątrz klasy publikowania i używać delegata z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="d3b9f-120">Jeśli używasz wersji ogólnej, nie potrzebujesz delegata niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="d3b9f-121">Zamiast tego w klasie publikowania należy `EventHandler<CustomEventArgs>`określić typ zdarzenia jako zastępując nazwę własnej klasy między nawiasami kąta.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="d3b9f-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="d3b9f-122">Example</span></span>  
 <span data-ttu-id="d3b9f-123">W poniższym przykładzie przedstawiono poprzednie kroki przy użyciu <xref:System.EventHandler%601> niestandardowej klasy EventArgs i jako typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d3b9f-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d3b9f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3b9f-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="d3b9f-125">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="d3b9f-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d3b9f-126">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d3b9f-126">Events</span></span>](./index.md)
- [<span data-ttu-id="d3b9f-127">Delegaty</span><span class="sxs-lookup"><span data-stu-id="d3b9f-127">Delegates</span></span>](../delegates/index.md)
