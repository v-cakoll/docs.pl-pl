---
title: Korzystanie z funkcji dopasowania wzorców w celu poszerzenia typów danych
description: W tym zaawansowanym samouczku pokazano, jak używać technik dopasowywania wzorców do tworzenia funkcji przy użyciu danych i algorytmów, które są tworzone osobno.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: fd08e707402bfcd552997111a9c3fa58841a5466
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240057"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="91a15-103">Samouczek: Używanie funkcji dopasowania wzorców do zwiększania typów danych</span><span class="sxs-lookup"><span data-stu-id="91a15-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="91a15-104">C#7 wprowadzono podstawowe funkcje dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="91a15-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="91a15-105">Te funkcje są rozszerzane C# w 8 przy użyciu nowych wyrażeń i wzorców.</span><span class="sxs-lookup"><span data-stu-id="91a15-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="91a15-106">Można napisać funkcję, która zachowuje się tak, jakby rozszerzone typy, które mogą znajdować się w innych bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="91a15-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="91a15-107">Innym zastosowaniem wzorców jest tworzenie funkcji wymaganych przez aplikację, która nie jest podstawową funkcją rozszerzania typu.</span><span class="sxs-lookup"><span data-stu-id="91a15-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="91a15-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="91a15-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="91a15-109">Rozpoznaj sytuacje, w których należy użyć dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="91a15-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="91a15-110">Używaj wyrażeń dopasowania wzorców, aby zaimplementować zachowanie na podstawie typów i wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a15-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="91a15-111">Połącz dopasowania wzorców z innymi technikami, aby utworzyć kompletne algorytmy.</span><span class="sxs-lookup"><span data-stu-id="91a15-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91a15-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="91a15-112">Prerequisites</span></span>

<span data-ttu-id="91a15-113">Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="91a15-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="91a15-114">C# 8 kompilator jest dostępny w programie [Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="91a15-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="91a15-115">W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91a15-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="91a15-116">Scenariusze dotyczące dopasowywania wzorców</span><span class="sxs-lookup"><span data-stu-id="91a15-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="91a15-117">Nowoczesne programowanie często obejmuje Integrowanie danych z wielu źródeł i prezentowanie informacji oraz uzyskiwanie wglądu w dane przy użyciu jednej spójnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91a15-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="91a15-118">Ty i Twój zespół nie będzie mieć kontroli ani dostępu dla wszystkich typów, które reprezentują dane przychodzące.</span><span class="sxs-lookup"><span data-stu-id="91a15-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="91a15-119">Klasyczny projekt zorientowany obiektowo wywoła do tworzenia typów w aplikacji, które reprezentują każdy typ danych z tych wielu źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="91a15-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="91a15-120">Następnie aplikacja będzie współpracować z tymi nowymi typami, konstruktorami dziedziczenia, tworzyć metody wirtualne i implementować abstrakcje.</span><span class="sxs-lookup"><span data-stu-id="91a15-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="91a15-121">Te techniki działają i czasami są najlepszymi narzędziami.</span><span class="sxs-lookup"><span data-stu-id="91a15-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="91a15-122">Innym razem można napisać mniej kodu.</span><span class="sxs-lookup"><span data-stu-id="91a15-122">Other times you can write less code.</span></span> <span data-ttu-id="91a15-123">Można napisać bardziej czysty kod przy użyciu technik, które dzielą dane z operacji, które manipulują tymi danymi.</span><span class="sxs-lookup"><span data-stu-id="91a15-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="91a15-124">W tym samouczku utworzysz i zbadasz aplikację, która pobiera dane przychodzące z kilku źródeł zewnętrznych w jednym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="91a15-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="91a15-125">Zobaczysz, jak **dopasowanie wzorca** zapewnia wydajny sposób użycia i przetwarzania tych danych w sposób, który nie jest częścią oryginalnego systemu.</span><span class="sxs-lookup"><span data-stu-id="91a15-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="91a15-126">Rozważmy główny obszar metropolitalnych, który korzysta z opłat i cen w czasie szczytu do zarządzania ruchem.</span><span class="sxs-lookup"><span data-stu-id="91a15-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="91a15-127">Napiszesz aplikację, która oblicza opłaty dla pojazdu na podstawie jego typu.</span><span class="sxs-lookup"><span data-stu-id="91a15-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="91a15-128">Późniejsze ulepszenia obejmują ceny na podstawie liczby osób w danym jeździe.</span><span class="sxs-lookup"><span data-stu-id="91a15-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="91a15-129">Dalsze ulepszenia zwiększają ceny na podstawie czasu i dnia tygodnia.</span><span class="sxs-lookup"><span data-stu-id="91a15-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="91a15-130">Z tego krótkiego opisu można szybko szkicować hierarchię obiektów, aby modelować ten system.</span><span class="sxs-lookup"><span data-stu-id="91a15-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="91a15-131">Jednak dane pochodzą z wielu źródeł, takich jak inne systemy zarządzania rejestracją pojazdów.</span><span class="sxs-lookup"><span data-stu-id="91a15-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="91a15-132">Te systemy zapewniają różne klasy do modelowania danych i nie masz modelu pojedynczego obiektu, którego można użyć.</span><span class="sxs-lookup"><span data-stu-id="91a15-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="91a15-133">W tym samouczku zostaną użyte te uproszczone klasy do modelowania danych pojazdu z tych systemów zewnętrznych, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="91a15-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="91a15-134">Możesz pobrać kod początkowy z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) .</span><span class="sxs-lookup"><span data-stu-id="91a15-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="91a15-135">Można zobaczyć, że klasy pojazdu pochodzą z różnych systemów i znajdują się w różnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="91a15-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="91a15-136">Nie można wykorzystać żadnej wspólnej klasy bazowej, innej niż `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="91a15-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="91a15-137">Projekty dopasowania wzorców</span><span class="sxs-lookup"><span data-stu-id="91a15-137">Pattern matching designs</span></span>

<span data-ttu-id="91a15-138">W scenariuszu używanym w tym samouczku przedstawiono rodzaje problemów, których dopasowanie do wzorców jest odpowiednie do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="91a15-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="91a15-139">Obiekty potrzebne do pracy nie należą do hierarchii obiektów pasujących do Twoich celów.</span><span class="sxs-lookup"><span data-stu-id="91a15-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="91a15-140">Być może pracujesz z klasami, które są częścią niepowiązanych systemów.</span><span class="sxs-lookup"><span data-stu-id="91a15-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="91a15-141">Dodawane funkcje nie są częścią abstrakcji rdzeni dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="91a15-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="91a15-142">Opłaty za przejazd przez pojazd *zmieniają* się w zależności od typu pojazdów, ale opłata nie jest podstawową funkcją pojazdu.</span><span class="sxs-lookup"><span data-stu-id="91a15-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="91a15-143">Gdy *kształt* danych i *operacje* na tych danych nie są opisane razem, funkcje dopasowania wzorców w programie C# ułatwiają pracę z.</span><span class="sxs-lookup"><span data-stu-id="91a15-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="91a15-144">Implementowanie podstawowych obliczeń opłat</span><span class="sxs-lookup"><span data-stu-id="91a15-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="91a15-145">Najbardziej podstawowe obliczenia płatne bazują wyłącznie na typie pojazdu:</span><span class="sxs-lookup"><span data-stu-id="91a15-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="91a15-146">`Car` to $2,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="91a15-147">`Taxi` to $3,50.</span><span class="sxs-lookup"><span data-stu-id="91a15-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="91a15-148">`Bus` to $5,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="91a15-149">`DeliveryTruck` to $10,00</span><span class="sxs-lookup"><span data-stu-id="91a15-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="91a15-150">Utwórz nową klasę `TollCalculator` i Implementuj dopasowanie wzorców na typie pojazdu, aby uzyskać kwotę opłaty.</span><span class="sxs-lookup"><span data-stu-id="91a15-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="91a15-151">Poniższy kod przedstawia początkową implementację `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="91a15-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="91a15-152">Poprzedni kod używa **wyrażenia Switch** (nie takiego samego jak instrukcja [`switch`](../language-reference/keywords/switch.md) ), które sprawdza **wzorzec typu**.</span><span class="sxs-lookup"><span data-stu-id="91a15-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="91a15-153">**Wyrażenie Switch** rozpoczyna się od zmiennej, `vehicle` w poprzednim kodzie, po którym następuje słowo kluczowe `switch`.</span><span class="sxs-lookup"><span data-stu-id="91a15-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="91a15-154">Następnie wszystkie **ramiona przełączania** są umieszczone w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="91a15-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="91a15-155">Wyrażenie `switch` wprowadza inne udoskonalenia do składni otaczającej instrukcję `switch`.</span><span class="sxs-lookup"><span data-stu-id="91a15-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="91a15-156">Słowo kluczowe `case` zostało pominięte, a wynikiem każdego ARM jest wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="91a15-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="91a15-157">Ostatnie dwie poręcze zawierają nową funkcję języka.</span><span class="sxs-lookup"><span data-stu-id="91a15-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="91a15-158">Przypadek `{ }` dopasowuje dowolny obiekt o wartości innej niż null, który nie jest zgodny z wcześniejszą ARM.</span><span class="sxs-lookup"><span data-stu-id="91a15-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="91a15-159">Ten ARM przechwytuje wszystkie nieprawidłowe typy przesłane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="91a15-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="91a15-160">Przypadek `{ }` musi być zgodny z przypadkami dla każdego typu pojazdu.</span><span class="sxs-lookup"><span data-stu-id="91a15-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="91a15-161">Jeśli zamówienie zostało cofnięte, pierwszeństwo ma `{ }` przypadku.</span><span class="sxs-lookup"><span data-stu-id="91a15-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="91a15-162">Na koniec wzorzec `null` wykrywa, kiedy `null` jest przenoszona do tej metody.</span><span class="sxs-lookup"><span data-stu-id="91a15-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="91a15-163">Wzorzec `null` może być ostatni, ponieważ wzorce innych typów pasują tylko do niezerowego obiektu o poprawnym typie.</span><span class="sxs-lookup"><span data-stu-id="91a15-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="91a15-164">Możesz przetestować ten kod przy użyciu następującego kodu w `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="91a15-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="91a15-165">Ten kod jest zawarty w projekcie początkowym, ale jest oznaczony jako komentarz. Usuń Komentarze i możesz sprawdzić, które z nich zapisano.</span><span class="sxs-lookup"><span data-stu-id="91a15-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="91a15-166">Zaczynasz widzieć, jak wzorce mogą pomóc w tworzeniu algorytmów, w których kod i dane są oddzielone.</span><span class="sxs-lookup"><span data-stu-id="91a15-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="91a15-167">Wyrażenie `switch` sprawdza typ i tworzy różne wartości na podstawie wyników.</span><span class="sxs-lookup"><span data-stu-id="91a15-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="91a15-168">To tylko początek.</span><span class="sxs-lookup"><span data-stu-id="91a15-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="91a15-169">Dodawanie cen użytkowania</span><span class="sxs-lookup"><span data-stu-id="91a15-169">Add occupancy pricing</span></span>

<span data-ttu-id="91a15-170">Urząd certyfikacji jest odpowiedzialny za przemieszczenie pojazdów z maksymalną wydajnością.</span><span class="sxs-lookup"><span data-stu-id="91a15-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="91a15-171">Zdecydowały się naliczać więcej czasu, gdy pojazdy mają mniej osób i zachęcają do pełnych pojazdów, oferując niższą cenę:</span><span class="sxs-lookup"><span data-stu-id="91a15-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="91a15-172">Samochody i taksówke bez pasażerów płatją dodatkową $0,50.</span><span class="sxs-lookup"><span data-stu-id="91a15-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="91a15-173">Samochody i taksówki z dwoma pasażerami otrzymują rabat w wysokości $0,50.</span><span class="sxs-lookup"><span data-stu-id="91a15-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="91a15-174">Samochody i taksówki z trzema lub większą liczbą osób uzyskują rabat $1,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="91a15-175">W przypadku magistrali, które mają mniej niż 50%, pełna opłata wynosi $2,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="91a15-176">Magistrale, które mają więcej niż 90%, uzyskają rabat $1,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="91a15-177">Te reguły można zaimplementować przy użyciu **wzorca właściwości** w tym samym wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="91a15-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="91a15-178">Wzorzec właściwości bada właściwości obiektu po ustaleniu typu.</span><span class="sxs-lookup"><span data-stu-id="91a15-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="91a15-179">Pojedynczy przypadek dla `Car` rozwija się do czterech różnych przypadków:</span><span class="sxs-lookup"><span data-stu-id="91a15-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="91a15-180">Pierwsze trzy przypadki testują typ jako `Car`, a następnie sprawdzają wartość właściwości `Passengers`.</span><span class="sxs-lookup"><span data-stu-id="91a15-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="91a15-181">Jeśli oba te wartości są zgodne, to wyrażenie jest oceniane i zwracane.</span><span class="sxs-lookup"><span data-stu-id="91a15-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="91a15-182">W podobny sposób można również rozwijać przypadki wypadków:</span><span class="sxs-lookup"><span data-stu-id="91a15-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="91a15-183">W poprzednim przykładzie klauzula `when` została pominięta w przypadku końcowym.</span><span class="sxs-lookup"><span data-stu-id="91a15-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="91a15-184">Następnie Zaimplementuj reguły użytkowania, rozszerzając przypadki dla magistrali, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91a15-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="91a15-185">Urząd opłat nie jest zaangażowany w liczbę pasażerów w wagonach dostawczych.</span><span class="sxs-lookup"><span data-stu-id="91a15-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="91a15-186">Zamiast tego dostosowują kwotę opłat w oparciu o klasę wagi wózków w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="91a15-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="91a15-187">Samochody ciężarowe przekraczające 5000 funtów są obciążane dodatkowymi $5,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="91a15-188">Wózki lekkie poniżej 3000 funtów otrzymują rabat $2,00.</span><span class="sxs-lookup"><span data-stu-id="91a15-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="91a15-189">Ta reguła jest zaimplementowana przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="91a15-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="91a15-190">Powyższy kod przedstawia klauzulę `when` ramienia przełącznika.</span><span class="sxs-lookup"><span data-stu-id="91a15-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="91a15-191">Za pomocą klauzuli `when` można testować warunki inne niż równość we właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a15-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="91a15-192">Po zakończeniu będziesz mieć metodę, która wygląda podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="91a15-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
    
    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

<span data-ttu-id="91a15-193">Wiele z tych broni przełączania to przykłady **wzorców cyklicznych**.</span><span class="sxs-lookup"><span data-stu-id="91a15-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="91a15-194">Na przykład `Car { Passengers: 1}` pokazuje stały wzorzec wewnątrz wzorca właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a15-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="91a15-195">Ten kod może być mniej powtarzany przy użyciu przełączników zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="91a15-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="91a15-196">W powyższych przykładach `Car` i `Taxi` mają cztery różne ramion.</span><span class="sxs-lookup"><span data-stu-id="91a15-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="91a15-197">W obu przypadkach można utworzyć wzorzec typu, który jest przesyłany do wzorca właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a15-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="91a15-198">Ta technika jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="91a15-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="91a15-199">W poprzednim przykładzie użycie wyrażenia cyklicznego oznacza, że nie należy powtarzać `Car` i `Taxi` ramion zawierających ramiona potomne, które testują wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="91a15-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="91a15-200">Ta technika nie jest używana dla broni `Bus` i `DeliveryTruck`, ponieważ te poręcze są zakresami testowania dla właściwości, a nie wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="91a15-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="91a15-201">Dodawanie cen szczytowych</span><span class="sxs-lookup"><span data-stu-id="91a15-201">Add peak pricing</span></span>

<span data-ttu-id="91a15-202">W przypadku ostatecznej funkcji urząd opłat umożliwia dodanie cen szczytowych z uwzględnieniem czasu.</span><span class="sxs-lookup"><span data-stu-id="91a15-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="91a15-203">W godzinach rano i wieczorem szczytu opłaty są napadane podwójnie.</span><span class="sxs-lookup"><span data-stu-id="91a15-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="91a15-204">Ta reguła ma wpływ tylko na ruch w jednym kierunku: przychodzące do miasta rano i wychodzące w godzinie wieczorem szczytu.</span><span class="sxs-lookup"><span data-stu-id="91a15-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="91a15-205">W innym czasie w ciągu dnia roboczego opłata zostanie zwiększona o 50%.</span><span class="sxs-lookup"><span data-stu-id="91a15-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="91a15-206">Późne i wczesne rano, opłaty są ograniczone o 25%.</span><span class="sxs-lookup"><span data-stu-id="91a15-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="91a15-207">W weekendie jest to normalna stawka, niezależnie od czasu.</span><span class="sxs-lookup"><span data-stu-id="91a15-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="91a15-208">Użyjesz dopasowania do wzorca dla tej funkcji, ale będziesz zintegrować ją z innymi technikami.</span><span class="sxs-lookup"><span data-stu-id="91a15-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="91a15-209">Można utworzyć wyrażenie dopasowania pojedynczego wzorca, które będzie uwzględniać wszystkie kombinacje kierunku, dzień tygodnia i godzinę.</span><span class="sxs-lookup"><span data-stu-id="91a15-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="91a15-210">Wynikiem będzie wyrażenie złożone.</span><span class="sxs-lookup"><span data-stu-id="91a15-210">The result would be a complicated expression.</span></span> <span data-ttu-id="91a15-211">Trudno jest czytać i trudny do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="91a15-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="91a15-212">Dzięki temu trudno jest zapewnić poprawność.</span><span class="sxs-lookup"><span data-stu-id="91a15-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="91a15-213">Zamiast tego Połącz te metody, aby utworzyć krotkę wartości, która zwięzłie opisuje wszystkie te Stany.</span><span class="sxs-lookup"><span data-stu-id="91a15-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="91a15-214">Następnie użyj dopasowania wzorca, aby obliczyć mnożnik dla opłaty za połączenie.</span><span class="sxs-lookup"><span data-stu-id="91a15-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="91a15-215">Krotka zawiera trzy warunki dyskretne:</span><span class="sxs-lookup"><span data-stu-id="91a15-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="91a15-216">Dzień jest dniem tygodnia lub weekendem.</span><span class="sxs-lookup"><span data-stu-id="91a15-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="91a15-217">Pasmo czasu, w którym jest zbierane połączenie płatne.</span><span class="sxs-lookup"><span data-stu-id="91a15-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="91a15-218">Kierunek znajduje się w mieście lub na zewnątrz miasta.</span><span class="sxs-lookup"><span data-stu-id="91a15-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="91a15-219">W poniższej tabeli przedstawiono kombinacje wartości wejściowych i mnożnik cen szczytowych:</span><span class="sxs-lookup"><span data-stu-id="91a15-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="91a15-220">Day</span><span class="sxs-lookup"><span data-stu-id="91a15-220">Day</span></span>        | <span data-ttu-id="91a15-221">Time</span><span class="sxs-lookup"><span data-stu-id="91a15-221">Time</span></span>         | <span data-ttu-id="91a15-222">Kierunek</span><span class="sxs-lookup"><span data-stu-id="91a15-222">Direction</span></span> | <span data-ttu-id="91a15-223">Premium</span><span class="sxs-lookup"><span data-stu-id="91a15-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="91a15-224">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-224">Weekday</span></span>    | <span data-ttu-id="91a15-225">rano szczytu</span><span class="sxs-lookup"><span data-stu-id="91a15-225">morning rush</span></span> | <span data-ttu-id="91a15-226">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-226">inbound</span></span>   | <span data-ttu-id="91a15-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="91a15-227">x 2.00</span></span>  |
| <span data-ttu-id="91a15-228">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-228">Weekday</span></span>    | <span data-ttu-id="91a15-229">rano szczytu</span><span class="sxs-lookup"><span data-stu-id="91a15-229">morning rush</span></span> | <span data-ttu-id="91a15-230">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-230">outbound</span></span>  | <span data-ttu-id="91a15-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-231">x 1.00</span></span>  |
| <span data-ttu-id="91a15-232">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-232">Weekday</span></span>    | <span data-ttu-id="91a15-233">telefonu</span><span class="sxs-lookup"><span data-stu-id="91a15-233">daytime</span></span>      | <span data-ttu-id="91a15-234">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-234">inbound</span></span>   | <span data-ttu-id="91a15-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="91a15-235">x 1.50</span></span>  |
| <span data-ttu-id="91a15-236">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-236">Weekday</span></span>    | <span data-ttu-id="91a15-237">telefonu</span><span class="sxs-lookup"><span data-stu-id="91a15-237">daytime</span></span>      | <span data-ttu-id="91a15-238">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-238">outbound</span></span>  | <span data-ttu-id="91a15-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="91a15-239">x 1.50</span></span>  |
| <span data-ttu-id="91a15-240">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-240">Weekday</span></span>    | <span data-ttu-id="91a15-241">szczytu wieczór</span><span class="sxs-lookup"><span data-stu-id="91a15-241">evening rush</span></span> | <span data-ttu-id="91a15-242">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-242">inbound</span></span>   | <span data-ttu-id="91a15-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-243">x 1.00</span></span>  |
| <span data-ttu-id="91a15-244">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-244">Weekday</span></span>    | <span data-ttu-id="91a15-245">szczytu wieczór</span><span class="sxs-lookup"><span data-stu-id="91a15-245">evening rush</span></span> | <span data-ttu-id="91a15-246">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-246">outbound</span></span>  | <span data-ttu-id="91a15-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="91a15-247">x 2.00</span></span>  |
| <span data-ttu-id="91a15-248">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-248">Weekday</span></span>    | <span data-ttu-id="91a15-249">Przelewy</span><span class="sxs-lookup"><span data-stu-id="91a15-249">overnight</span></span>    | <span data-ttu-id="91a15-250">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-250">inbound</span></span>   | <span data-ttu-id="91a15-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="91a15-251">x 0.75</span></span>  |
| <span data-ttu-id="91a15-252">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="91a15-252">Weekday</span></span>    | <span data-ttu-id="91a15-253">Przelewy</span><span class="sxs-lookup"><span data-stu-id="91a15-253">overnight</span></span>    | <span data-ttu-id="91a15-254">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-254">outbound</span></span>  | <span data-ttu-id="91a15-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="91a15-255">x 0.75</span></span>  |
| <span data-ttu-id="91a15-256">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-256">Weekend</span></span>    | <span data-ttu-id="91a15-257">rano szczytu</span><span class="sxs-lookup"><span data-stu-id="91a15-257">morning rush</span></span> | <span data-ttu-id="91a15-258">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-258">inbound</span></span>   | <span data-ttu-id="91a15-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-259">x 1.00</span></span>  |
| <span data-ttu-id="91a15-260">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-260">Weekend</span></span>    | <span data-ttu-id="91a15-261">rano szczytu</span><span class="sxs-lookup"><span data-stu-id="91a15-261">morning rush</span></span> | <span data-ttu-id="91a15-262">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-262">outbound</span></span>  | <span data-ttu-id="91a15-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-263">x 1.00</span></span>  |
| <span data-ttu-id="91a15-264">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-264">Weekend</span></span>    | <span data-ttu-id="91a15-265">telefonu</span><span class="sxs-lookup"><span data-stu-id="91a15-265">daytime</span></span>      | <span data-ttu-id="91a15-266">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-266">inbound</span></span>   | <span data-ttu-id="91a15-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-267">x 1.00</span></span>  |
| <span data-ttu-id="91a15-268">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-268">Weekend</span></span>    | <span data-ttu-id="91a15-269">telefonu</span><span class="sxs-lookup"><span data-stu-id="91a15-269">daytime</span></span>      | <span data-ttu-id="91a15-270">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-270">outbound</span></span>  | <span data-ttu-id="91a15-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-271">x 1.00</span></span>  |
| <span data-ttu-id="91a15-272">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-272">Weekend</span></span>    | <span data-ttu-id="91a15-273">szczytu wieczór</span><span class="sxs-lookup"><span data-stu-id="91a15-273">evening rush</span></span> | <span data-ttu-id="91a15-274">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-274">inbound</span></span>   | <span data-ttu-id="91a15-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-275">x 1.00</span></span>  |
| <span data-ttu-id="91a15-276">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-276">Weekend</span></span>    | <span data-ttu-id="91a15-277">szczytu wieczór</span><span class="sxs-lookup"><span data-stu-id="91a15-277">evening rush</span></span> | <span data-ttu-id="91a15-278">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-278">outbound</span></span>  | <span data-ttu-id="91a15-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-279">x 1.00</span></span>  |
| <span data-ttu-id="91a15-280">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-280">Weekend</span></span>    | <span data-ttu-id="91a15-281">Przelewy</span><span class="sxs-lookup"><span data-stu-id="91a15-281">overnight</span></span>    | <span data-ttu-id="91a15-282">dotycząc</span><span class="sxs-lookup"><span data-stu-id="91a15-282">inbound</span></span>   | <span data-ttu-id="91a15-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-283">x 1.00</span></span>  |
| <span data-ttu-id="91a15-284">Weekend</span><span class="sxs-lookup"><span data-stu-id="91a15-284">Weekend</span></span>    | <span data-ttu-id="91a15-285">Przelewy</span><span class="sxs-lookup"><span data-stu-id="91a15-285">overnight</span></span>    | <span data-ttu-id="91a15-286">wyjściowy</span><span class="sxs-lookup"><span data-stu-id="91a15-286">outbound</span></span>  | <span data-ttu-id="91a15-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="91a15-287">x 1.00</span></span>  |

<span data-ttu-id="91a15-288">Istnieją 16 różnych kombinacji trzech zmiennych.</span><span class="sxs-lookup"><span data-stu-id="91a15-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="91a15-289">Łącząc niektóre warunki, można uprościć ostateczne wyrażenie Switch.</span><span class="sxs-lookup"><span data-stu-id="91a15-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="91a15-290">System, który zbiera opłaty za usługę, używa struktury <xref:System.DateTime> na czas, w którym nastąpiła opłata.</span><span class="sxs-lookup"><span data-stu-id="91a15-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="91a15-291">Kompiluj metody Członkowskie, które tworzą zmienne z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="91a15-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="91a15-292">Poniższa funkcja używa wyrażenia przełącznika dopasowania wzorca, aby określić, czy <xref:System.DateTime> reprezentuje weekend czy dzień tygodnia:</span><span class="sxs-lookup"><span data-stu-id="91a15-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="91a15-293">Ta metoda działa, ale jest repetitious.</span><span class="sxs-lookup"><span data-stu-id="91a15-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="91a15-294">Można uprościć ten sposób, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="91a15-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="91a15-295">Następnie Dodaj podobną funkcję, aby przydzielić czas do bloków:</span><span class="sxs-lookup"><span data-stu-id="91a15-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="91a15-296">Poprzednia metoda nie używa dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="91a15-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="91a15-297">Jest to wyraźniejsze użycie znanych kaskadowych instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="91a15-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="91a15-298">Należy dodać prywatny `enum`, aby przekonwertować każdy zakres czasu na wartość dyskretną.</span><span class="sxs-lookup"><span data-stu-id="91a15-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="91a15-299">Po utworzeniu tych metod można użyć innego wyrażenia `switch` ze **wzorcem spójności** , aby obliczyć cenę Premium.</span><span class="sxs-lookup"><span data-stu-id="91a15-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="91a15-300">Można utworzyć wyrażenie `switch` ze wszystkimi 16 bronią:</span><span class="sxs-lookup"><span data-stu-id="91a15-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="91a15-301">Powyższy kod działa, ale można go uprościć.</span><span class="sxs-lookup"><span data-stu-id="91a15-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="91a15-302">Wszystkie osiem kombinacji dla weekendu mają te same opłaty za połączenie płatne.</span><span class="sxs-lookup"><span data-stu-id="91a15-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="91a15-303">Można zastąpić wszystkie osiem następującymi wierszami:</span><span class="sxs-lookup"><span data-stu-id="91a15-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="91a15-304">Ruch przychodzący i wychodzący ma ten sam mnożnik w ciągu dnia tygodnia Daytime i w godzinach nocnych.</span><span class="sxs-lookup"><span data-stu-id="91a15-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="91a15-305">Te cztery broń przełączania można zastąpić następującymi dwoma wierszami:</span><span class="sxs-lookup"><span data-stu-id="91a15-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="91a15-306">Kod powinien wyglądać podobnie do następującego kodu po obu tych zmianach:</span><span class="sxs-lookup"><span data-stu-id="91a15-306">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="91a15-307">Na koniec możesz usunąć dwie szczytu godziny, które będą obciążane stałą cenę.</span><span class="sxs-lookup"><span data-stu-id="91a15-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="91a15-308">Po usunięciu tych broni można zastąpić `false` odrzucanie (`_`) w końcowej aktywacji.</span><span class="sxs-lookup"><span data-stu-id="91a15-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="91a15-309">Następująca metoda została zakończona:</span><span class="sxs-lookup"><span data-stu-id="91a15-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="91a15-310">Ten przykład wyróżnia jedną z zalet dopasowania do wzorca: gałęzie wzorców są oceniane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="91a15-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="91a15-311">W przypadku zmiany rozmieszczenia w taki sposób, aby wcześniejsza gałąź obsługiwała jeden z przyszłych przypadków, kompilator ostrzega o nieosiągalnym kodzie.</span><span class="sxs-lookup"><span data-stu-id="91a15-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="91a15-312">Te reguły języka ułatwiają wykonywanie powyższych uproszczeń bez obaw, że kod nie uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="91a15-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="91a15-313">Dopasowanie wzorców sprawia, że niektóre typy kodu są bardziej czytelne i oferują alternatywę dla technik zorientowanych obiektowo, gdy nie można dodać kodu do klas.</span><span class="sxs-lookup"><span data-stu-id="91a15-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="91a15-314">Chmura powoduje, że dane i funkcje mogą się na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="91a15-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="91a15-315">*Kształt* danych i *operacje* na nim nie są koniecznie opisane razem.</span><span class="sxs-lookup"><span data-stu-id="91a15-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="91a15-316">W tym samouczku wykorzystano istniejące dane w sposób całkowicie różny od oryginalnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="91a15-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="91a15-317">Dopasowywanie do wzorca daje możliwość zapisu funkcji, która overrode te typy, nawet jeśli nie można ich zwiększyć.</span><span class="sxs-lookup"><span data-stu-id="91a15-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="91a15-318">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="91a15-318">Next steps</span></span>

<span data-ttu-id="91a15-319">Gotowy kod można pobrać z repozytorium usługi GitHub [/przykłady](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) .</span><span class="sxs-lookup"><span data-stu-id="91a15-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="91a15-320">Eksploruj własne wzorce i Dodaj tę technikę do zwykłych działań związanych z kodowaniem.</span><span class="sxs-lookup"><span data-stu-id="91a15-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="91a15-321">Uczenie tych technik umożliwia innym sposobem podejścia problemów i tworzenia nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="91a15-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
