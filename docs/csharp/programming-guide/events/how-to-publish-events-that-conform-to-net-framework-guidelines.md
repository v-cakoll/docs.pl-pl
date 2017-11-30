---
title: "Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 570729e432146b4ef97e4c487f644b12b354bb4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="cbc76-102">Porady: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cbc76-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="cbc76-103">W poniższej procedurze przedstawiono sposób dodawania zdarzenia, które są zgodne ze standardem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorzec do klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="cbc76-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="cbc76-104">Wszystkie zdarzenia w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas są oparte na <xref:System.EventHandler> delegata, która jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="cbc76-104">All events in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="cbc76-105">[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Przedstawiono ogólny wersji tego obiektu delegowanego <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="cbc76-105">The [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="cbc76-106">Następujące przykłady przedstawiają sposób użycia obie wersje.</span><span class="sxs-lookup"><span data-stu-id="cbc76-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="cbc76-107">Mimo że zdarzeń w klasach zdefiniowanych przez użytkownika może być oparta na dowolnego typu delegata prawidłowe nawet pełnomocników, które zwracają wartości, jest zwykle zalecane na podstawie zdarzeń [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] wzorca za pomocą <xref:System.EventHandler>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cbc76-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="cbc76-108">Aby opublikować zdarzenia oparte na wzorcu EventHandler</span><span class="sxs-lookup"><span data-stu-id="cbc76-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="cbc76-109">(Pomiń ten krok i przejdź do kroku 3a, jeśli nie masz do wysyłania danych niestandardowych z wydarzenia). Zadeklarować klasy w niestandardowych danych w zakresie, widocznego dla obu wydawcy i subskrybenta klasy.</span><span class="sxs-lookup"><span data-stu-id="cbc76-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="cbc76-110">Następnie dodaj członków wymagane do przechowywania danych zdarzenia niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cbc76-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="cbc76-111">W tym przykładzie zostanie zwrócony ciąg proste.</span><span class="sxs-lookup"><span data-stu-id="cbc76-111">In this example, a simple string is returned.</span></span>  
  
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
  
2.  <span data-ttu-id="cbc76-112">(Ten krok można pominąć, jeśli używasz wersji ogólnego <xref:System.EventHandler%601> .) Zadeklarować obiektu delegowanego w klasie publikowania.</span><span class="sxs-lookup"><span data-stu-id="cbc76-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="cbc76-113">Nadaj nazwę, która kończy się *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="cbc76-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="cbc76-114">Drugi parametr określa typ EventArgs swojego niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="cbc76-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="cbc76-115">Deklarowanie zdarzenia w klasie publikowania za pomocą jednej z następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="cbc76-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="cbc76-116">Jeśli masz nie niestandardowej klasy EventArgs danego typu zdarzenia będą delegata EventHandler nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="cbc76-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="cbc76-117">Nie należy deklarować delegata, ponieważ jest już zadeklarowany w <xref:System> przestrzeni nazw, która jest dołączana w przypadku tworzenia projektu C#.</span><span class="sxs-lookup"><span data-stu-id="cbc76-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="cbc76-118">Dodaj następujący kod do klasy wydawcy.</span><span class="sxs-lookup"><span data-stu-id="cbc76-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="cbc76-119">Jeśli używasz wersji nieogólnego <xref:System.EventHandler> i mieć niestandardowej klasy pochodzącej od <xref:System.EventArgs>, zadeklarować wydarzenia w klasie publikowania i używana jako typ pełnomocnika w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="cbc76-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="cbc76-120">Jeśli używasz wersji ogólnego, nie trzeba niestandardowego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="cbc76-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="cbc76-121">Zamiast tego w klasie publikowania, musisz wybrać typ użytkownika zdarzeń jako `EventHandler<CustomEventArgs>`, zastępując nazwę klasy między nawiasami.</span><span class="sxs-lookup"><span data-stu-id="cbc76-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="cbc76-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbc76-122">Example</span></span>  
 <span data-ttu-id="cbc76-123">W poniższym przykładzie pokazano poprzednich kroków za pomocą niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cbc76-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cbc76-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbc76-124">See Also</span></span>  
 <xref:System.Delegate>  
 [<span data-ttu-id="cbc76-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cbc76-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cbc76-126">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cbc76-126">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="cbc76-127">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="cbc76-127">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
