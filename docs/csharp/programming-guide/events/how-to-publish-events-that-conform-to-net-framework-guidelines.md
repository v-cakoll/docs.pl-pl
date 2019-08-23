---
title: 'Instrukcje: Publikuj zdarzenia zgodne z wytycznymi .NET Framework — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cf0f57caad41da0a29b935029731260154a2dc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924025"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="58d95-102">Instrukcje: Publikuj zdarzenia zgodne z wytycznymi .NET Framework (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="58d95-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="58d95-103">Poniższa procedura pokazuje, jak dodać zdarzenia, które obserwują standardowy wzorzec .NET Framework do klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="58d95-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="58d95-104">Wszystkie zdarzenia w bibliotece klas .NET Framework są oparte na <xref:System.EventHandler> delegatze, który jest zdefiniowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="58d95-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="58d95-105">W .NET Framework 2,0 wprowadzono ogólną wersję tego delegata <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="58d95-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="58d95-106">W poniższych przykładach pokazano, jak używać obu wersji.</span><span class="sxs-lookup"><span data-stu-id="58d95-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="58d95-107">Chociaż zdarzenia w zdefiniowanych klasach mogą opierać się na dowolnym prawidłowym typie delegata, nawet delegatów zwracających wartość, zazwyczaj zaleca się oparcie zdarzeń na wzorcu .NET Framework przy użyciu <xref:System.EventHandler>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="58d95-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="58d95-108">Aby opublikować zdarzenia na podstawie wzorca EventHandler</span><span class="sxs-lookup"><span data-stu-id="58d95-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="58d95-109">(Pomiń ten krok i przejdź do kroku 3a, jeśli nie musisz wysyłać niestandardowych danych do zdarzenia). Zadeklaruj klasę niestandardowych danych w zakresie, który jest widoczny dla obu klas wydawcy i subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="58d95-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="58d95-110">Następnie Dodaj wymagane elementy członkowskie, aby przechowywać dane niestandardowego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="58d95-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="58d95-111">W tym przykładzie jest zwracany prosty ciąg.</span><span class="sxs-lookup"><span data-stu-id="58d95-111">In this example, a simple string is returned.</span></span>  
  
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
  
2. <span data-ttu-id="58d95-112">(Pomiń ten krok, jeśli używasz ogólnej wersji programu <xref:System.EventHandler%601> ). Zadeklaruj delegat w klasie publikacji.</span><span class="sxs-lookup"><span data-stu-id="58d95-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="58d95-113">Nadaj mu nazwę kończącą się na *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="58d95-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="58d95-114">Drugi parametr określa niestandardowy typ EventArgs.</span><span class="sxs-lookup"><span data-stu-id="58d95-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="58d95-115">Zadeklaruj zdarzenie w klasie publikacji przy użyciu jednego z następujących kroków.</span><span class="sxs-lookup"><span data-stu-id="58d95-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="58d95-116">Jeśli nie masz niestandardowej klasy EventArgs, typ zdarzenia będzie nieogólnym delegatem EventHandler.</span><span class="sxs-lookup"><span data-stu-id="58d95-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="58d95-117">Nie trzeba deklarować delegata, ponieważ jest on już zadeklarowany w <xref:System> przestrzeni nazw, która jest uwzględniona podczas tworzenia C# projektu.</span><span class="sxs-lookup"><span data-stu-id="58d95-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="58d95-118">Dodaj następujący kod do klasy wydawcy.</span><span class="sxs-lookup"><span data-stu-id="58d95-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="58d95-119">Jeśli używasz nieogólnej wersji programu <xref:System.EventHandler> i masz klasę niestandardową pochodną od <xref:System.EventArgs>, zadeklaruj zdarzenie wewnątrz klasy publikacji i użyj delegata z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="58d95-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="58d95-120">Jeśli używasz wersji ogólnej, nie potrzebujesz niestandardowego delegata.</span><span class="sxs-lookup"><span data-stu-id="58d95-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="58d95-121">Zamiast tego w klasie publikacji należy określić typ zdarzenia jako `EventHandler<CustomEventArgs>`, zastępując nazwę własnej klasy między nawiasami kątowymi.</span><span class="sxs-lookup"><span data-stu-id="58d95-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="58d95-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="58d95-122">Example</span></span>  
 <span data-ttu-id="58d95-123">Poniższy przykład demonstruje poprzednie kroki przy użyciu niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="58d95-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="58d95-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58d95-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="58d95-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="58d95-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="58d95-126">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="58d95-126">Events</span></span>](./index.md)
- [<span data-ttu-id="58d95-127">Delegaty</span><span class="sxs-lookup"><span data-stu-id="58d95-127">Delegates</span></span>](../delegates/index.md)
