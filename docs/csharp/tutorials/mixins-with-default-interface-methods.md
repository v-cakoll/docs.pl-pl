---
title: Tworzenie typów domieszki przy użyciu domyślnych metod interfejsu
description: Przy użyciu domyślnych elementów członkowskich interfejsu można rozciągnąć interfejsy z opcjonalnymi implementacjami domyślnymi dla realizatorów.
ms.date: 10/04/2019
ms.openlocfilehash: 4dee97226420139d9cd09ad75d7c8caf4967273d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321625"
---
# <a name="tutorial-mix-in-functionality-when-creating-classes-using-interfaces-with-default-interface-methods"></a><span data-ttu-id="94fc2-103">Samouczek: mieszanie funkcji podczas tworzenia klas przy użyciu interfejsów z domyślnymi metodami interfejsu</span><span class="sxs-lookup"><span data-stu-id="94fc2-103">Tutorial: Mix in functionality when creating classes using interfaces with default interface methods</span></span>

<span data-ttu-id="94fc2-104">Począwszy od C# 8,0 na platformie .net Core 3,0, można zdefiniować implementację w przypadku deklarowania elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94fc2-104">Beginning with C# 8.0 on .NET Core 3.0, you can define an implementation when you declare a member of an interface.</span></span> <span data-ttu-id="94fc2-105">Ta funkcja udostępnia nowe możliwości, w których można definiować domyślne implementacje funkcji zadeklarowanych w interfejsach.</span><span class="sxs-lookup"><span data-stu-id="94fc2-105">This feature provides new capabilities where you can define default implementations for features declared in interfaces.</span></span> <span data-ttu-id="94fc2-106">Klasy mogą być wybierane podczas przesłonięcia funkcji, kiedy używać funkcji domyślnych i gdy nie należy deklarować obsługi funkcji dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-106">Classes can pick when to override functionality, when to use the default functionality, and when not to declare support for discrete features.</span></span>

<span data-ttu-id="94fc2-107">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="94fc2-107">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="94fc2-108">Utwórz interfejsy z implementacjami opisującymi funkcje dyskretne.</span><span class="sxs-lookup"><span data-stu-id="94fc2-108">Create interfaces with implementations that describe discrete features.</span></span>
> * <span data-ttu-id="94fc2-109">Utwórz klasy, które używają domyślnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-109">Create classes that use the default implementations.</span></span>
> * <span data-ttu-id="94fc2-110">Utwórz klasy, które zastępują niektóre lub wszystkie domyślne implementacje.</span><span class="sxs-lookup"><span data-stu-id="94fc2-110">Create classes that override some or all of the default implementations.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94fc2-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="94fc2-111">Prerequisites</span></span>

<span data-ttu-id="94fc2-112">Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="94fc2-112">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="94fc2-113">Kompilator C# 8,0 jest dostępny od wersji [Visual Studio 2019, 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="94fc2-113">The C# 8.0 compiler is available starting with [Visual Studio 2019, 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>

## <a name="limitations-of-extension-methods"></a><span data-ttu-id="94fc2-114">Ograniczenia metod rozszerzających</span><span class="sxs-lookup"><span data-stu-id="94fc2-114">Limitations of extension methods</span></span>

<span data-ttu-id="94fc2-115">Jednym ze sposobów implementacji zachowania, które pojawia się jako część interfejsu, jest zdefiniowanie [metod rozszerzających](../programming-guide/classes-and-structs/extension-methods.md) , które zapewniają zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="94fc2-115">One way you can implement behavior that appears as part of an interface is to define [extension methods](../programming-guide/classes-and-structs/extension-methods.md) that provide the default behavior.</span></span> <span data-ttu-id="94fc2-116">Interfejsy deklarują minimalny zestaw elementów członkowskich, zapewniając większą powierzchnię dla każdej klasy, która implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="94fc2-116">Interfaces declare a minimum set of members while providing a greater surface area for any class that implements that interface.</span></span> <span data-ttu-id="94fc2-117">Na przykład metody rozszerzające w <xref:System.Linq.Enumerable> zapewniają implementację dowolnej sekwencji jako źródła zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="94fc2-117">For example, the extension methods in <xref:System.Linq.Enumerable> provide the implementation for any sequence to be the source of a LINQ query.</span></span>

<span data-ttu-id="94fc2-118">Metody rozszerzające są rozwiązane w czasie kompilacji, przy użyciu zadeklarowanego typu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="94fc2-118">Extension methods are resolved at compile time, using the declared type of the variable.</span></span> <span data-ttu-id="94fc2-119">Klasy implementujące interfejs mogą zapewnić lepszą implementację dowolnej metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="94fc2-119">Classes that implement the interface can provide a better implementation for any extension method.</span></span> <span data-ttu-id="94fc2-120">Deklaracje zmiennych muszą być zgodne z typem implementującym, aby umożliwić kompilatorowi wybranie tej implementacji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-120">Variable declarations must match the implementing type to enable the compiler to choose that implementation.</span></span> <span data-ttu-id="94fc2-121">Gdy typ czasu kompilacji jest zgodny z interfejsem, wywołania metody są rozpoznawane jako Metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="94fc2-121">When the compile-time type matches the interface, method calls resolve to the extension method.</span></span> <span data-ttu-id="94fc2-122">Innym problemem z metodami rozszerzania jest to, że te metody są dostępne wszędzie tam, gdzie klasy zawierającej metody rozszerzające są dostępne.</span><span class="sxs-lookup"><span data-stu-id="94fc2-122">Another concern with extension methods is that those methods are accessible wherever the class containing the extension methods is accessible.</span></span> <span data-ttu-id="94fc2-123">Klasy nie mogą deklarować, jeśli powinny lub nie muszą dostarczać funkcji zadeklarowanych w metodach rozszerzających.</span><span class="sxs-lookup"><span data-stu-id="94fc2-123">Classes cannot declare if they should or should not provide features declared in extension methods.</span></span>

<span data-ttu-id="94fc2-124">Począwszy od C# 8,0, można zadeklarować domyślne implementacje jako metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94fc2-124">Starting with C# 8.0, you can declare the default implementations as interface methods.</span></span> <span data-ttu-id="94fc2-125">Następnie każda klasa automatycznie używa implementacji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="94fc2-125">Then, every class automatically uses the default implementation.</span></span> <span data-ttu-id="94fc2-126">Każda klasa, która może zapewnić lepszą implementację, może przesłonić definicję metody interfejsu lepszym algorytmem.</span><span class="sxs-lookup"><span data-stu-id="94fc2-126">Any class that can provide a better implementation can override the interface method definition with a better algorithm.</span></span> <span data-ttu-id="94fc2-127">W jednym sensie ta technika jest podobna do sposobu używania [metod rozszerzających](../programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="94fc2-127">In one sense, this technique sounds similar to how you could use [extension methods](../programming-guide/classes-and-structs/extension-methods.md).</span></span>

<span data-ttu-id="94fc2-128">W tym artykule dowiesz się, jak domyślne implementacje interfejsu umożliwiają tworzenie nowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="94fc2-128">In this article, you'll learn how default interface implementations enable new scenarios.</span></span>

## <a name="design-the-application"></a><span data-ttu-id="94fc2-129">Projektowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="94fc2-129">Design the application</span></span>

<span data-ttu-id="94fc2-130">Weź pod uwagę aplikację Automatyzacja domu.</span><span class="sxs-lookup"><span data-stu-id="94fc2-130">Consider a home automation application.</span></span> <span data-ttu-id="94fc2-131">Prawdopodobnie masz wiele różnych typów świateł i wskaźników, które mogą być używane w całej firmie.</span><span class="sxs-lookup"><span data-stu-id="94fc2-131">You probably have many different types of lights and indicators that could be used throughout the house.</span></span> <span data-ttu-id="94fc2-132">Każde światło musi obsługiwać interfejsy API, aby je włączyć i wyłączyć oraz zgłosić bieżący stan.</span><span class="sxs-lookup"><span data-stu-id="94fc2-132">Every light must support APIs to turn them on and off, and to report the current state.</span></span> <span data-ttu-id="94fc2-133">Niektóre sygnalizatory i wskaźniki mogą obsługiwać inne funkcje, takie jak:</span><span class="sxs-lookup"><span data-stu-id="94fc2-133">Some lights and indicators may support other features, such as:</span></span>

- <span data-ttu-id="94fc2-134">Włącz światło, a następnie wyłącz je po upłynięciu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="94fc2-134">Turn light on, then turn it off after a timer.</span></span>
- <span data-ttu-id="94fc2-135">Miganie światła przez pewien czas.</span><span class="sxs-lookup"><span data-stu-id="94fc2-135">Blink the light for a period of time.</span></span>

<span data-ttu-id="94fc2-136">Niektóre z tych rozszerzonych możliwości mogą być emulowane na urządzeniach, które obsługują minimalny zestaw.</span><span class="sxs-lookup"><span data-stu-id="94fc2-136">Some of these extended capabilities could be emulated in devices that support the minimal set.</span></span> <span data-ttu-id="94fc2-137">Wskazuje to na podanie domyślnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-137">That indicates providing a default implementation.</span></span> <span data-ttu-id="94fc2-138">W przypadku urządzeń, które mają więcej funkcji wbudowanych, oprogramowanie urządzenia może korzystać z natywnych funkcji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-138">For those devices that have more capabilities built in, the device software would use the native capabilities.</span></span> <span data-ttu-id="94fc2-139">W przypadku innych sygnalizatorów mogą oni wybrać implementację interfejsu i użyć domyślnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-139">For other lights, they could choose to implement the interface and use the default implementation.</span></span>

<span data-ttu-id="94fc2-140">Domyślnymi elementami członkowskimi interfejsu jest lepszym rozwiązaniem dla tego scenariusza niż metody rozszerzające.</span><span class="sxs-lookup"><span data-stu-id="94fc2-140">Default interface members is a better solution for this scenario than extension methods.</span></span> <span data-ttu-id="94fc2-141">Autorzy klasy mogą kontrolować interfejsy, które wybierają do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="94fc2-141">Class authors can control which interfaces they choose to implement.</span></span> <span data-ttu-id="94fc2-142">Wybrane interfejsy są dostępne jako metody.</span><span class="sxs-lookup"><span data-stu-id="94fc2-142">Those interfaces they choose are available as methods.</span></span> <span data-ttu-id="94fc2-143">Ponadto, ponieważ domyślne metody interfejsu są domyślnie wirtualne, metoda wysyłania zawsze wybiera implementację w klasie.</span><span class="sxs-lookup"><span data-stu-id="94fc2-143">In addition, because default interface methods are virtual by default, the method dispatch always chooses the implementation in the class.</span></span> 

<span data-ttu-id="94fc2-144">Utwórzmy kod, aby przedstawić te różnice.</span><span class="sxs-lookup"><span data-stu-id="94fc2-144">Let's create the code to demonstrate these differences.</span></span>

## <a name="create-interfaces"></a><span data-ttu-id="94fc2-145">Tworzenie interfejsów</span><span class="sxs-lookup"><span data-stu-id="94fc2-145">Create interfaces</span></span>

<span data-ttu-id="94fc2-146">Zacznij od utworzenia interfejsu, który definiuje zachowanie dla wszystkich świateł:</span><span class="sxs-lookup"><span data-stu-id="94fc2-146">Start by creating the interface that defines the behavior for all lights:</span></span>

[!code-csharp[Declare base interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetILightInterfaceV1)]

<span data-ttu-id="94fc2-147">W przypadku podstawowego narzutu, armatura uproszczona może zaimplementować ten interfejs, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="94fc2-147">A basic overhead light fixture might implement this interface as shown in the following code:</span></span>

[!code-csharp[First overhead light](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetOverheadLightV1)]

<span data-ttu-id="94fc2-148">W tym samouczku kod nie obejmuje urządzeń IoT, ale emuluje te działania przez zapisanie komunikatów do konsoli.</span><span class="sxs-lookup"><span data-stu-id="94fc2-148">In this tutorial, the code doesn't drive IoT devices, but emulates those activities by writing messages to the console.</span></span> <span data-ttu-id="94fc2-149">Możesz eksplorować kod bez automatyzowania domu.</span><span class="sxs-lookup"><span data-stu-id="94fc2-149">You can explore the code without automating your house.</span></span>

<span data-ttu-id="94fc2-150">Następnie zdefiniujemy interfejs dla światła, który może być automatycznie wyłączany po upływie limitu czasu:</span><span class="sxs-lookup"><span data-stu-id="94fc2-150">Next, let's define the interface for a light that can automatically turn off after a timeout:</span></span>

[!code-csharp[pure Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/UnusedExampleCode.cs?name=SnippetPureTimerInterface)]

<span data-ttu-id="94fc2-151">Można dodać podstawową implementację do światła narzutowego, ale lepszym rozwiązaniem jest zmodyfikowanie tej definicji interfejsu w celu udostępnienia domyślnej implementacji `virtual`:</span><span class="sxs-lookup"><span data-stu-id="94fc2-151">You could add a basic implementation to the overhead light, but a better solution is to modify this interface definition to provide a `virtual` default implementation:</span></span>

[!code-csharp[Timer interface](~/samples/csharp/tutorials/mixins-with-interfaces/ITimerLight.cs?name=SnippetTimerLightFinal)]

<span data-ttu-id="94fc2-152">Po dodaniu tej zmiany Klasa `OverheadLight` może zaimplementować funkcję Timer, deklarując obsługę interfejsu:</span><span class="sxs-lookup"><span data-stu-id="94fc2-152">By adding that change, the `OverheadLight` class can implement the timer function by declaring support for the interface:</span></span>

```csharp
public class OverheadLight : ITimerLight { }
```

<span data-ttu-id="94fc2-153">Inny typ oświetlenia może obsługiwać bardziej zaawansowany protokół.</span><span class="sxs-lookup"><span data-stu-id="94fc2-153">A different light type may support a more sophisticated protocol.</span></span> <span data-ttu-id="94fc2-154">Może ona zapewnić własną implementację `TurnOnFor`, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="94fc2-154">It can provide its own implementation for `TurnOnFor`, as shown in the following code:</span></span>

[!code-csharp[Override the timer function](~/samples/csharp/tutorials/mixins-with-interfaces/HalogenLight.cs?name=SnippetHalogenLight)]

<span data-ttu-id="94fc2-155">W przeciwieństwie do zastępowania metod klasy wirtualnej, deklaracja `TurnOnFor` w klasie `HalogenLight` nie używa słowa kluczowego `override`.</span><span class="sxs-lookup"><span data-stu-id="94fc2-155">Unlike overriding virtual class methods, the declaration of `TurnOnFor` in the `HalogenLight` class does not use the `override` keyword.</span></span> 

## <a name="mix-and-match-capabilities"></a><span data-ttu-id="94fc2-156">Możliwości mieszania i dopasowywania</span><span class="sxs-lookup"><span data-stu-id="94fc2-156">Mix and match capabilities</span></span>

<span data-ttu-id="94fc2-157">Zalety domyślnych metod interfejsu stają się wyraźniejsze, ponieważ wprowadzasz bardziej zaawansowane możliwości.</span><span class="sxs-lookup"><span data-stu-id="94fc2-157">The advantages of default interface methods become clearer as you introduce more advanced capabilities.</span></span> <span data-ttu-id="94fc2-158">Używanie interfejsów umożliwia mieszanie i dopasowywanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-158">Using interfaces enables you to mix and match capabilities.</span></span> <span data-ttu-id="94fc2-159">Umożliwia również każdemu autorowi klasy wybór między implementacją domyślną a implementacją niestandardową.</span><span class="sxs-lookup"><span data-stu-id="94fc2-159">It also enables each class author to choose between the default implementation and a custom implementation.</span></span> <span data-ttu-id="94fc2-160">Dodajmy interfejs z domyślną implementacją dla migających świateł:</span><span class="sxs-lookup"><span data-stu-id="94fc2-160">Let's add an interface with a default implementation for a blinking light:</span></span>

[!code-csharp[Define the blinking light interface](~/samples/csharp/tutorials/mixins-with-interfaces/IBlinkingLight.cs?name=SnippetBlinkingLight)]

<span data-ttu-id="94fc2-161">Domyślna implementacja umożliwia migotanie.</span><span class="sxs-lookup"><span data-stu-id="94fc2-161">The default implementation enables any light to blink.</span></span> <span data-ttu-id="94fc2-162">Światełko narzutu można dodać czasomierz i migające możliwości przy użyciu domyślnej implementacji:</span><span class="sxs-lookup"><span data-stu-id="94fc2-162">The overhead light can add both timer and blink capabilities using the default implementation:</span></span>

[!code-csharp[Use the default blink function](~/samples/csharp/tutorials/mixins-with-interfaces/OverheadLight.cs?name=SnippetOverheadLight)]

<span data-ttu-id="94fc2-163">Nowy typ światła, `LEDLight` obsługuje zarówno funkcję Timer, jak i funkcję Blink.</span><span class="sxs-lookup"><span data-stu-id="94fc2-163">A new light type, the `LEDLight` supports both the timer function and the blink function directly.</span></span> <span data-ttu-id="94fc2-164">Ten styl jasny implementuje interfejsy `ITimerLight` i `IBlinkingLight` i przesłania metodę `Blink`:</span><span class="sxs-lookup"><span data-stu-id="94fc2-164">This light style implements both the `ITimerLight` and `IBlinkingLight` interfaces, and overrides the `Blink` method:</span></span>

[!code-csharp[Override the blink function](~/samples/csharp/tutorials/mixins-with-interfaces/LEDLight.cs?name=SnippetLEDLight)]

<span data-ttu-id="94fc2-165">@No__t-0 może obsługiwać jednocześnie funkcje migotania i czasomierza:</span><span class="sxs-lookup"><span data-stu-id="94fc2-165">An `ExtraFancyLight` might support both blink and timer functions directly:</span></span>

[!code-csharp[Override the blink and timer function](~/samples/csharp/tutorials/mixins-with-interfaces/ExtraFancyLight.cs?name=SnippetExtraFancyLight)]

<span data-ttu-id="94fc2-166">Utworzony wcześniej `HalogenLight` nie obsługuje migania.</span><span class="sxs-lookup"><span data-stu-id="94fc2-166">The `HalogenLight` you created earlier doesn't support blinking.</span></span> <span data-ttu-id="94fc2-167">Dlatego nie należy dodawać `IBlinkingLight` do listy obsługiwanych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="94fc2-167">So, don't add the `IBlinkingLight` to the list of its supported interfaces.</span></span>

## <a name="detect-the-light-types-using-pattern-matching"></a><span data-ttu-id="94fc2-168">Wykrywanie typów świateł przy użyciu dopasowania wzorca</span><span class="sxs-lookup"><span data-stu-id="94fc2-168">Detect the light types using pattern matching</span></span>

<span data-ttu-id="94fc2-169">Następnie Napiszmy kod testowy.</span><span class="sxs-lookup"><span data-stu-id="94fc2-169">Next, let's write some test code.</span></span> <span data-ttu-id="94fc2-170">Możesz użyć C#funkcji [dopasowania do wzorca](../pattern-matching.md) , aby określić możliwości światła, sprawdzając, które interfejsy obsługuje.</span><span class="sxs-lookup"><span data-stu-id="94fc2-170">You can make use of C#'s [pattern matching](../pattern-matching.md) feature to determine a light's capabilities by examining which interfaces it supports.</span></span>  <span data-ttu-id="94fc2-171">Poniższa metoda korzysta z obsługiwanych funkcji poszczególnych świateł:</span><span class="sxs-lookup"><span data-stu-id="94fc2-171">The following method exercises the supported capabilities of each light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetTestLightFunctions)]

<span data-ttu-id="94fc2-172">Poniższy kod w metodzie `Main` tworzy każdy typ światła w sekwencji i testy, które są jasne:</span><span class="sxs-lookup"><span data-stu-id="94fc2-172">The following code in your `Main` method creates each light type in sequence and tests that light:</span></span>

[!code-csharp[Test a light's capabilities](~/samples/csharp/tutorials/mixins-with-interfaces/Program.cs?name=SnippetMainMethod)]

## <a name="how-the-compiler-determines-best-implementation"></a><span data-ttu-id="94fc2-173">Jak kompilator określa najlepszą implementację</span><span class="sxs-lookup"><span data-stu-id="94fc2-173">How the compiler determines best implementation</span></span>

<span data-ttu-id="94fc2-174">W tym scenariuszu przedstawiono interfejs podstawowy bez żadnych implementacji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-174">This scenario shows a base interface without any implementations.</span></span> <span data-ttu-id="94fc2-175">Dodanie metody do interfejsu `ILight` wprowadza nowe złożoności.</span><span class="sxs-lookup"><span data-stu-id="94fc2-175">Adding a method into the `ILight` interface introduces new complexities.</span></span> <span data-ttu-id="94fc2-176">Reguły języka rządzące domyślnymi metodami interfejsu minimalizują wpływ konkretnych klas, które implementują wiele interfejsów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-176">The language rules governing default interface methods minimize the effect on the concrete classes that implement multiple derived interfaces.</span></span> <span data-ttu-id="94fc2-177">Zwiększmy oryginalny interfejs za pomocą nowej metody, aby zobaczyć, jak zmienia się jej użycie.</span><span class="sxs-lookup"><span data-stu-id="94fc2-177">Let's enhance the original interface with a new method to show how that changes its use.</span></span> <span data-ttu-id="94fc2-178">Każdy sygnalizator wskaźnika może zgłosić swój stan mocy jako wartość wyliczaną:</span><span class="sxs-lookup"><span data-stu-id="94fc2-178">Every indicator light can report its power status as an enumerated value:</span></span>

[!code-csharp[Enumeration for power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetPowerStatus)]

<span data-ttu-id="94fc2-179">Domyślna implementacja zakłada zasilanie AC:</span><span class="sxs-lookup"><span data-stu-id="94fc2-179">The default implementation assumes AC power:</span></span>

[!code-csharp[Report a default power status](~/samples/csharp/tutorials/mixins-with-interfaces/ILight.cs?name=SnippetILightInterface)]

<span data-ttu-id="94fc2-180">Te zmiany kompilują się w sposób przejrzysty, mimo że `ExtraFancyLight` deklaruje obsługę interfejsu `ILight` i obu interfejsów pochodnych, `ITimerLight` i `IBlinkingLight`.</span><span class="sxs-lookup"><span data-stu-id="94fc2-180">These changes compile cleanly, even though the `ExtraFancyLight` declares support for the `ILight` interface and both derived interfaces, `ITimerLight` and `IBlinkingLight`.</span></span> <span data-ttu-id="94fc2-181">W interfejsie `ILight` jest zadeklarowana tylko jedna implementacja "najbliższy".</span><span class="sxs-lookup"><span data-stu-id="94fc2-181">There's only one "closest" implementation declared in the `ILight` interface.</span></span> <span data-ttu-id="94fc2-182">Każda klasa, która zadeklarowała przesłonięcie, stanie się jedną "najbliższą" implementacją.</span><span class="sxs-lookup"><span data-stu-id="94fc2-182">Any class that declared an override would become the one "closest" implementation.</span></span> <span data-ttu-id="94fc2-183">Przykłady z poprzednich klas, które overrodeą elementy członkowskie innych interfejsów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-183">You saw examples in the preceding classes that overrode the members of other derived interfaces.</span></span>

<span data-ttu-id="94fc2-184">Unikaj zastępowania tej samej metody w wielu interfejsach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-184">Avoid overriding the same method in multiple derived interfaces.</span></span> <span data-ttu-id="94fc2-185">Wykonanie tej operacji tworzy niejednoznaczne wywołanie metody za każdym razem, gdy klasa implementuje oba interfejsy pochodne.</span><span class="sxs-lookup"><span data-stu-id="94fc2-185">Doing so creates an ambiguous method call whenever a class implements both derived interfaces.</span></span> <span data-ttu-id="94fc2-186">Kompilator nie może wybrać jednej lepszej metody, aby wystawić błąd.</span><span class="sxs-lookup"><span data-stu-id="94fc2-186">The compiler can't pick a single better method so it issues an error.</span></span> <span data-ttu-id="94fc2-187">Na przykład jeśli dla `IBlinkingLight` i `ITimerLight` zaimplementowano przesłonięcie `PowerStatus`, `OverheadLight` musi dostarczyć bardziej szczegółowe przesłonięcie.</span><span class="sxs-lookup"><span data-stu-id="94fc2-187">For example, if both the `IBlinkingLight` and `ITimerLight` implemented an override of `PowerStatus`, the `OverheadLight` would need to provide a more specific override.</span></span> <span data-ttu-id="94fc2-188">W przeciwnym razie kompilator nie może wybrać między implementacjami w dwóch interfejsach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-188">Otherwise, the compiler can't pick between the implementations in the two derived interfaces.</span></span> <span data-ttu-id="94fc2-189">Zazwyczaj można uniknąć tej sytuacji, zachowując definicje interfejsu jako małe i skoncentrowane na jednej funkcji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-189">You can usually avoid this situation by keeping interface definitions small and focused on one feature.</span></span> <span data-ttu-id="94fc2-190">W tym scenariuszu każda funkcja światła jest własnym interfejsem; wiele interfejsów jest dziedziczonych tylko przez klasy.</span><span class="sxs-lookup"><span data-stu-id="94fc2-190">In this scenario, each capability of a light is its own interface; multiple interfaces are only inherited by classes.</span></span>

<span data-ttu-id="94fc2-191">Ten przykład pokazuje jeden scenariusz, w którym można zdefiniować osobne funkcje, które mogą być mieszane w klasy.</span><span class="sxs-lookup"><span data-stu-id="94fc2-191">This sample shows one scenario where you can define discrete features that can be mixed into classes.</span></span> <span data-ttu-id="94fc2-192">Deklaruje dowolny zestaw obsługiwanych funkcji, deklarując interfejsy obsługiwane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="94fc2-192">You declare any set of supported functionality by declaring which interfaces a class supports.</span></span> <span data-ttu-id="94fc2-193">Użycie wirtualnych metod interfejsu wirtualnego umożliwia używanie klas lub Definiowanie innej implementacji dla dowolnych lub wszystkich metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="94fc2-193">The use of virtual default interface methods enables classes to use or define a different implementation for any or all the interface methods.</span></span> <span data-ttu-id="94fc2-194">Ta funkcja językowa udostępnia nowe sposoby modelowania kompilowanych systemów rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="94fc2-194">This language capability provides new ways to model the real-world systems you're building.</span></span> <span data-ttu-id="94fc2-195">Domyślne metody interfejsu zapewniają wyraźniejszy sposób wyznaczania pokrewnych klas, które mogą mieszać i odpowiadać różnym funkcjom przy użyciu wirtualnych implementacji tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="94fc2-195">Default interface methods provide a clearer way to express related classes that may mix and match different features using virtual implementations of those capabilities.</span></span>