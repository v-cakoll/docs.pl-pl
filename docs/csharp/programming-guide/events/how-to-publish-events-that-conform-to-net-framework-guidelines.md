---
title: Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework — Przewodnik programowania w języku C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144802"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="f018d-102">Jak opublikować zdarzenia zgodne z zaleceniami .NET Framework (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f018d-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="f018d-103">Poniższa procedura pokazuje, jak dodać zdarzenia, które obserwują standardowy wzorzec .NET Framework do klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="f018d-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="f018d-104">Wszystkie zdarzenia w bibliotece klas .NET Framework są oparte na <xref:System.EventHandler> delegatze, który jest zdefiniowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f018d-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="f018d-105">W .NET Framework 2,0 wprowadzono ogólną wersję tego delegata <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="f018d-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="f018d-106">W poniższych przykładach pokazano, jak używać obu wersji.</span><span class="sxs-lookup"><span data-stu-id="f018d-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="f018d-107">Chociaż zdarzenia w zdefiniowanych klasach mogą opierać się na dowolnym prawidłowym typie delegata, nawet delegatów zwracających wartość, zazwyczaj zaleca się oparcie zdarzeń na wzorcu .NET Framework przy użyciu <xref:System.EventHandler> , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f018d-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="f018d-108">Nazwa `EventHandler` może prowadzić do nieprawidłowych pomyłek, ponieważ nie jest w rzeczywistości obsługiwana dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f018d-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="f018d-109"><xref:System.EventHandler>, I ogólne <xref:System.EventHandler%601> są typami delegatów.</span><span class="sxs-lookup"><span data-stu-id="f018d-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="f018d-110">Metoda lub wyrażenie lambda, którego sygnatura jest zgodna z definicją delegata, jest *obsługą zdarzeń* i zostanie wywołana, gdy zdarzenie zostanie zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="f018d-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="f018d-111">Aby opublikować zdarzenia na podstawie wzorca EventHandler</span><span class="sxs-lookup"><span data-stu-id="f018d-111">To publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="f018d-112">(Pomiń ten krok i przejdź do kroku 3a, jeśli nie musisz wysyłać niestandardowych danych do zdarzenia). Zadeklaruj klasę niestandardowych danych w zakresie, który jest widoczny dla obu klas wydawcy i subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="f018d-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="f018d-113">Następnie Dodaj wymagane elementy członkowskie, aby przechowywać dane niestandardowego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f018d-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="f018d-114">W tym przykładzie jest zwracany prosty ciąg.</span><span class="sxs-lookup"><span data-stu-id="f018d-114">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="f018d-115">(Pomiń ten krok, jeśli używasz ogólnej wersji programu <xref:System.EventHandler%601> ). Zadeklaruj delegat w klasie publikacji.</span><span class="sxs-lookup"><span data-stu-id="f018d-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="f018d-116">Nadaj jej nazwę kończącą się na `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="f018d-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="f018d-117">Drugi parametr określa `EventArgs` typ niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="f018d-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="f018d-118">Zadeklaruj zdarzenie w klasie publikacji przy użyciu jednego z następujących kroków.</span><span class="sxs-lookup"><span data-stu-id="f018d-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="f018d-119">Jeśli nie masz niestandardowej klasy EventArgs, typ zdarzenia będzie nieogólnym delegatem EventHandler.</span><span class="sxs-lookup"><span data-stu-id="f018d-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="f018d-120">Nie trzeba deklarować delegata, ponieważ jest on już zadeklarowany w <xref:System> przestrzeni nazw, która jest uwzględniona podczas tworzenia projektu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="f018d-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="f018d-121">Dodaj następujący kod do klasy wydawcy.</span><span class="sxs-lookup"><span data-stu-id="f018d-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="f018d-122">Jeśli używasz nieogólnej wersji programu <xref:System.EventHandler> i masz klasę niestandardową pochodną od <xref:System.EventArgs> , zadeklaruj zdarzenie wewnątrz klasy publikacji i użyj delegata z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="f018d-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="f018d-123">Jeśli używasz wersji ogólnej, nie potrzebujesz niestandardowego delegata.</span><span class="sxs-lookup"><span data-stu-id="f018d-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="f018d-124">Zamiast tego w klasie publikacji należy określić typ zdarzenia jako `EventHandler<CustomEventArgs>` , zastępując nazwę własnej klasy między nawiasami kątowymi.</span><span class="sxs-lookup"><span data-stu-id="f018d-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="f018d-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f018d-125">Example</span></span>

<span data-ttu-id="f018d-126">Poniższy przykład demonstruje poprzednie kroki przy użyciu niestandardowej klasy EventArgs i <xref:System.EventHandler%601> jako typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f018d-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="f018d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f018d-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="f018d-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f018d-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f018d-129">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f018d-129">Events</span></span>](index.md)
- [<span data-ttu-id="f018d-130">Delegaci</span><span class="sxs-lookup"><span data-stu-id="f018d-130">Delegates</span></span>](../delegates/index.md)
