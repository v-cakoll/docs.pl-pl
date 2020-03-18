---
title: Rozszerzanie typów danych za pomocą funkcji dopasowywania wzorców
description: Ten zaawansowany samouczek pokazuje, jak używać technik dopasowywania wzorców do tworzenia funkcji przy użyciu danych i algorytmów, które są tworzone oddzielnie.
ms.date: 03/13/2019
ms-technology: csharp-whats-new
ms.custom: mvc
ms.openlocfilehash: df1054d8e0ec2b2539e6a1d00bf353d8ca927397
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156535"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="83118-103">Samouczek: Korzystanie z funkcji dopasowywania wzorców w celu rozszerzenia typów danych</span><span class="sxs-lookup"><span data-stu-id="83118-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="83118-104">C# 7 wprowadzono podstawowe funkcje dopasowywania wzorców.</span><span class="sxs-lookup"><span data-stu-id="83118-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="83118-105">Te funkcje są rozszerzone w języku C# 8 z nowych wyrażeń i wzorców.</span><span class="sxs-lookup"><span data-stu-id="83118-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="83118-106">Można napisać funkcje, które zachowują się tak, jakby rozszerzone typy, które mogą znajdować się w innych bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="83118-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="83118-107">Innym zastosowaniem wzorców jest tworzenie funkcji, które aplikacja wymaga, która nie jest podstawową funkcją typu jest rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="83118-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="83118-108">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="83118-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="83118-109">Rozpoznaj sytuacje, w których należy używać dopasowywania wzorców.</span><span class="sxs-lookup"><span data-stu-id="83118-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="83118-110">Użyj wyrażenia dopasowywania wzorców, aby zaimplementować zachowanie na podstawie typów i wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="83118-111">Połącz dopasowywanie wzorców z innymi technikami, aby utworzyć kompletne algorytmy.</span><span class="sxs-lookup"><span data-stu-id="83118-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="83118-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="83118-112">Prerequisites</span></span>

<span data-ttu-id="83118-113">Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="83118-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="83118-114">Kompilator C# 8 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="83118-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="83118-115">W tym samouczku przyjęto założenie, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="83118-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="83118-116">Scenariusze dopasowywania wzorców</span><span class="sxs-lookup"><span data-stu-id="83118-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="83118-117">Nowoczesny rozwój często obejmuje integrację danych z wielu źródeł oraz prezentowanie informacji i spostrzeżeń z tych danych w jednej, spoistej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="83118-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="83118-118">Ty i Twój zespół nie będziecie mieli kontroli ani dostępu dla wszystkich typów reprezentujących przychodzące dane.</span><span class="sxs-lookup"><span data-stu-id="83118-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="83118-119">Klasyczny projekt obiektowy będzie wywoływać tworzenie typów w aplikacji, które reprezentują każdy typ danych z tych wielu źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="83118-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="83118-120">Następnie aplikacja będzie działać z tych nowych typów, budować hierarchie dziedziczenia, tworzenie metod wirtualnych i implementować abstrakcje.</span><span class="sxs-lookup"><span data-stu-id="83118-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="83118-121">Te techniki działają, a czasami są najlepszymi narzędziami.</span><span class="sxs-lookup"><span data-stu-id="83118-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="83118-122">Innym razem można napisać mniej kodu.</span><span class="sxs-lookup"><span data-stu-id="83118-122">Other times you can write less code.</span></span> <span data-ttu-id="83118-123">Można napisać bardziej przejrzysty kod przy użyciu technik, które oddzielają dane od operacji, które manipulują tymi danymi.</span><span class="sxs-lookup"><span data-stu-id="83118-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="83118-124">W tym samouczku utworzysz i eksplorujesz aplikację, która pobiera dane przychodzące z kilku źródeł zewnętrznych dla jednego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="83118-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="83118-125">Zobaczysz, jak **dopasowanie wzorca** zapewnia skuteczny sposób używania i przetwarzania tych danych w sposób, który nie był częścią oryginalnego systemu.</span><span class="sxs-lookup"><span data-stu-id="83118-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="83118-126">Rozważmy główny obszar metropolitalny, który korzysta z opłat drogowych i cen w godzinach szczytu do zarządzania ruchem.</span><span class="sxs-lookup"><span data-stu-id="83118-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="83118-127">Piszesz aplikację, która oblicza opłaty za pojazd na podstawie jego typu.</span><span class="sxs-lookup"><span data-stu-id="83118-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="83118-128">Późniejsze ulepszenia obejmują ceny oparte na liczbie osób znajdujących się w pojeździe.</span><span class="sxs-lookup"><span data-stu-id="83118-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="83118-129">Dalsze ulepszenia dodają ceny na podstawie czasu i dnia tygodnia.</span><span class="sxs-lookup"><span data-stu-id="83118-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="83118-130">Z tego krótkiego opisu być może szybko naszkicowaliście hierarchię obiektów, aby modelować ten system.</span><span class="sxs-lookup"><span data-stu-id="83118-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="83118-131">Jednak twoje dane pochodzą z wielu źródeł, takich jak inne systemy zarządzania rejestracją pojazdów.</span><span class="sxs-lookup"><span data-stu-id="83118-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="83118-132">Systemy te zapewniają różne klasy do modelu tych danych i nie masz jednego modelu obiektu, którego można użyć.</span><span class="sxs-lookup"><span data-stu-id="83118-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="83118-133">W tym samouczku użyjesz tych uproszczonych klas do modelowania danych pojazdu z tych systemów zewnętrznych, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="83118-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="83118-134">Kod startowy można pobrać z repozytorium GitHub/sample.You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span><span class="sxs-lookup"><span data-stu-id="83118-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="83118-135">Widać, że klasy pojazdów są z różnych systemów i znajdują się w różnych przestrzeniach nazw.</span><span class="sxs-lookup"><span data-stu-id="83118-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="83118-136">Nie wspólnej klasy podstawowej, inne niż `System.Object` mogą być lewarowane.</span><span class="sxs-lookup"><span data-stu-id="83118-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="83118-137">Wzory pasujące do wzorców</span><span class="sxs-lookup"><span data-stu-id="83118-137">Pattern matching designs</span></span>

<span data-ttu-id="83118-138">Scenariusz użyty w tym samouczku podkreśla rodzaje problemów, które dopasowywanie wzorców jest dobrze nadaje się do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="83118-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="83118-139">Obiekty, z którymi musisz pracować, nie znajdują się w hierarchii obiektów, która pasuje do twoich celów.</span><span class="sxs-lookup"><span data-stu-id="83118-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="83118-140">Być może pracujesz z klasami, które są częścią niepowiązanych systemów.</span><span class="sxs-lookup"><span data-stu-id="83118-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="83118-141">Funkcje, które dodajesz nie jest częścią podstawowej abstrakcji dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="83118-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="83118-142">Opłata za przejazd pobierana przez pojazd *zmienia się* w przypadku różnych typów pojazdów, ale opłata za przejazd nie jest podstawową funkcją pojazdu.</span><span class="sxs-lookup"><span data-stu-id="83118-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="83118-143">Gdy *kształt* danych i *operacje* na tych danych nie są opisane razem, funkcje dopasowywania wzorców w języku C# ułatwiają pracę z.</span><span class="sxs-lookup"><span data-stu-id="83118-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="83118-144">Wdrożenie podstawowych obliczeń opłat drogowych</span><span class="sxs-lookup"><span data-stu-id="83118-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="83118-145">Najbardziej podstawowe obliczenie opłaty drogowej zależy tylko od typu pojazdu:</span><span class="sxs-lookup"><span data-stu-id="83118-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="83118-146">A `Car` wynosi $2.00.</span><span class="sxs-lookup"><span data-stu-id="83118-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="83118-147">A `Taxi` wynosi $3.50.</span><span class="sxs-lookup"><span data-stu-id="83118-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="83118-148">A `Bus` wynosi $5.00.</span><span class="sxs-lookup"><span data-stu-id="83118-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="83118-149">A `DeliveryTruck` jest $10.00</span><span class="sxs-lookup"><span data-stu-id="83118-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="83118-150">Utwórz `TollCalculator` nową klasę i zaimplementuj dopasowanie wzorców na typie pojazdu, aby uzyskać kwotę opłaty drogowej.</span><span class="sxs-lookup"><span data-stu-id="83118-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="83118-151">Poniższy kod przedstawia wstępną `TollCalculator`implementację pliku .</span><span class="sxs-lookup"><span data-stu-id="83118-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="83118-152">Poprzedni kod używa **wyrażenia przełącznika** (nie [`switch`](../language-reference/keywords/switch.md) takie samo jak instrukcja), która testuje **wzorzec typu**.</span><span class="sxs-lookup"><span data-stu-id="83118-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="83118-153">**Wyrażenie przełącznika** rozpoczyna się `vehicle` od zmiennej w poprzednim `switch` kodzie, po której następuje słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="83118-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="83118-154">Następnie przychodzi wszystkie **ramiona przełącznika** wewnątrz kręcone szelki.</span><span class="sxs-lookup"><span data-stu-id="83118-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="83118-155">Wyrażenie `switch` sprawia, że inne udoskonalenia do `switch` składni, która otacza instrukcję.</span><span class="sxs-lookup"><span data-stu-id="83118-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="83118-156">Słowo `case` kluczowe jest pomijane, a wynik każdego ramienia jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="83118-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="83118-157">Ostatnie dwa ramiona pokazują nową funkcję językową.</span><span class="sxs-lookup"><span data-stu-id="83118-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="83118-158">Sprawa `{ }` pasuje do dowolnego obiektu innego niż null, który nie był zgodny z wcześniejszym ramieniem.</span><span class="sxs-lookup"><span data-stu-id="83118-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="83118-159">To ramię przechwytuje wszelkie niepoprawne typy przekazane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="83118-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="83118-160">Sprawa `{ }` musi być zgodna z przypadkami dla każdego typu pojazdu.</span><span class="sxs-lookup"><span data-stu-id="83118-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="83118-161">Gdyby zamówienie zostało odwrócone, `{ }` sprawa miałaby pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="83118-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="83118-162">Na koniec `null` wzorzec `null` wykrywa, gdy a jest przekazywana do tej metody.</span><span class="sxs-lookup"><span data-stu-id="83118-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="83118-163">Wzorzec `null` może być ostatni, ponieważ inne wzorce typu odpowiadają tylko obiektowi inne niż null poprawnego typu.</span><span class="sxs-lookup"><span data-stu-id="83118-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="83118-164">Można przetestować ten kod za `Program.cs`pomocą następującego kodu w:</span><span class="sxs-lookup"><span data-stu-id="83118-164">You can test this code using the following code in `Program.cs`:</span></span>

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

<span data-ttu-id="83118-165">Ten kod jest uwzględniony w projekcie startowym, ale jest komentowany. Usuń komentarze i możesz sprawdzić, co napisałeś.</span><span class="sxs-lookup"><span data-stu-id="83118-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="83118-166">Zaczynasz widzieć, jak wzorce mogą pomóc w tworzeniu algorytmów, w których kod i dane są oddzielne.</span><span class="sxs-lookup"><span data-stu-id="83118-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="83118-167">Wyrażenie `switch` testuje typ i generuje różne wartości na podstawie wyników.</span><span class="sxs-lookup"><span data-stu-id="83118-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="83118-168">To dopiero początek.</span><span class="sxs-lookup"><span data-stu-id="83118-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="83118-169">Dodaj ceny obłożenia</span><span class="sxs-lookup"><span data-stu-id="83118-169">Add occupancy pricing</span></span>

<span data-ttu-id="83118-170">Organ pobierający opłaty drogowe chce zachęcić pojazdy do poruszania się z maksymalną przepustowością.</span><span class="sxs-lookup"><span data-stu-id="83118-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="83118-171">Zdecydowali się pobierać wyższe opłaty, gdy pojazdy mają mniej pasażerów, i zachęcać do pełnych pojazdów, oferując niższe ceny:</span><span class="sxs-lookup"><span data-stu-id="83118-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="83118-172">Samochody i taksówki bez pasażerów zapłacić dodatkowe 0,50 dolarów.</span><span class="sxs-lookup"><span data-stu-id="83118-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="83118-173">Samochody i taksówki z dwoma pasażerami otrzymują zniżkę w wysokości 0,50 USD.</span><span class="sxs-lookup"><span data-stu-id="83118-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="83118-174">Samochody i taksówki z trzema lub więcej pasażerami otrzymują zniżkę w wysokości 1,00 USD.</span><span class="sxs-lookup"><span data-stu-id="83118-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="83118-175">Autobusy, które są mniej niż 50% pełne zapłacić dodatkowe 2,00 dolarów.</span><span class="sxs-lookup"><span data-stu-id="83118-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="83118-176">Autobusy, które są więcej niż 90% pełne dostać 1,00 dolarów zniżki.</span><span class="sxs-lookup"><span data-stu-id="83118-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="83118-177">Reguły te można zaimplementować przy użyciu **wzorca właściwości** w tym samym wyrażeniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="83118-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="83118-178">Wzorzec właściwości sprawdza właściwości obiektu po określeniu typu.</span><span class="sxs-lookup"><span data-stu-id="83118-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="83118-179">Pojedynczy przypadek dla `Car` rozszerza się do czterech różnych przypadków:</span><span class="sxs-lookup"><span data-stu-id="83118-179">The single case for a `Car` expands to four different cases:</span></span>

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

<span data-ttu-id="83118-180">Pierwsze trzy przypadki przetestować `Car`typ jako , a `Passengers` następnie sprawdzić wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="83118-181">Jeśli oba zgodne, to wyrażenie jest oceniane i zwracane.</span><span class="sxs-lookup"><span data-stu-id="83118-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="83118-182">Można również rozszerzyć sprawy dotyczące taksówek w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="83118-182">You would also expand the cases for taxis in a similar manner:</span></span>

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

<span data-ttu-id="83118-183">W poprzednim przykładzie klauzula `when` została pominięta w ostatnim przypadku.</span><span class="sxs-lookup"><span data-stu-id="83118-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="83118-184">Następnie należy wdrożyć zasady obłożenia, rozszerzając sprawy dla autobusów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="83118-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="83118-185">Organ pobierający opłaty nie zajmuje się liczbą pasażerów w samochodach dostawczych.</span><span class="sxs-lookup"><span data-stu-id="83118-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="83118-186">Zamiast tego dostosowują kwotę opłaty drogowej na podstawie klasy wagowej samochodów ciężarowych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="83118-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="83118-187">Samochody ciężarowe powyżej 5000 funtów są płatne dodatkowe 5,00 dolarów.</span><span class="sxs-lookup"><span data-stu-id="83118-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="83118-188">Lekkie ciężarówki poniżej 3000 funtów otrzymują zniżkę w wysokości 2,00 USD.</span><span class="sxs-lookup"><span data-stu-id="83118-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="83118-189">Ta reguła jest implementowana przy następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="83118-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="83118-190">Poprzedni kod zawiera `when` klauzulę ramienia przełącznika.</span><span class="sxs-lookup"><span data-stu-id="83118-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="83118-191">Klauzula `when` służy do testowania warunków innych niż równości we właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="83118-192">Po zakończeniu będziesz mieć metodę, która wygląda podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="83118-192">When you've finished, you'll have a method that looks much like the following:</span></span>

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

<span data-ttu-id="83118-193">Wiele z tych ramion przełącznika są przykładami **rekurencyjne wzory**.</span><span class="sxs-lookup"><span data-stu-id="83118-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="83118-194">Na przykład `Car { Passengers: 1}` pokazuje stały wzorzec wewnątrz wzorca właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="83118-195">Można sprawić, że ten kod będzie mniej powtarzalny przy użyciu przełączników zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="83118-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="83118-196">Oba `Car` `Taxi` mają cztery różne ramiona w poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="83118-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="83118-197">W obu przypadkach można utworzyć wzorzec typu, który zasila wzorzec właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="83118-198">Ta technika jest pokazana w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="83118-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="83118-199">W poprzednim przykładzie użycie wyrażenia cyklicznego oznacza, że nie powtarzasz `Car` i `Taxi` ramion zawierających ramiona podrzędne, które testują wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="83118-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="83118-200">Ta technika nie jest `Bus` `DeliveryTruck` używana dla i broni, ponieważ te ramiona są zakresy testowania właściwości, a nie wartości dyskretne.</span><span class="sxs-lookup"><span data-stu-id="83118-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="83118-201">Dodawanie cen szczytowych</span><span class="sxs-lookup"><span data-stu-id="83118-201">Add peak pricing</span></span>

<span data-ttu-id="83118-202">W przypadku końcowej funkcji urząd opłat drogowych chce dodać ceny szczytowe zależne od czasu.</span><span class="sxs-lookup"><span data-stu-id="83118-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="83118-203">W godzinach porannych i wieczornych w godzinach szczytu opłaty są podwojone.</span><span class="sxs-lookup"><span data-stu-id="83118-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="83118-204">Zasada ta wpływa tylko na ruch w jednym kierunku: przychodzące do miasta rano, a wychodzące w godzinach szczytu wieczorem.</span><span class="sxs-lookup"><span data-stu-id="83118-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="83118-205">W innych okresach dnia pracy opłaty drogowe wzrastają o 50%.</span><span class="sxs-lookup"><span data-stu-id="83118-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="83118-206">Późną nocą i wczesnym rankiem opłaty drogowe są zmniejszane o 25%.</span><span class="sxs-lookup"><span data-stu-id="83118-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="83118-207">W weekend, jest to normalna stawka, niezależnie od czasu.</span><span class="sxs-lookup"><span data-stu-id="83118-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="83118-208">Użyjesz dopasowywania wzorców dla tej funkcji, ale zintegrujesz ją z innymi technikami.</span><span class="sxs-lookup"><span data-stu-id="83118-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="83118-209">Można utworzyć wyrażenie dopasowania pojedynczego wzorca, które uwzględniałoby wszystkie kombinacje kierunku, dnia tygodnia i godziny.</span><span class="sxs-lookup"><span data-stu-id="83118-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="83118-210">Rezultatem byłoby skomplikowane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="83118-210">The result would be a complicated expression.</span></span> <span data-ttu-id="83118-211">Byłoby to trudne do odczytania i trudne do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="83118-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="83118-212">To sprawia, że trudno jest zapewnić poprawność.</span><span class="sxs-lookup"><span data-stu-id="83118-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="83118-213">Zamiast tego połączyć te metody, aby zbudować krotkę wartości, które zwięźle opisuje wszystkie te stany.</span><span class="sxs-lookup"><span data-stu-id="83118-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="83118-214">Następnie użyj dopasowania wzorca, aby obliczyć mnożnik dla opłaty drogowej.</span><span class="sxs-lookup"><span data-stu-id="83118-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="83118-215">Krotka zawiera trzy dyskretne warunki:</span><span class="sxs-lookup"><span data-stu-id="83118-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="83118-216">Dzień to dzień powszedni lub weekend.</span><span class="sxs-lookup"><span data-stu-id="83118-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="83118-217">Pasmo czasu, w którym pobierana jest opłata drogowa.</span><span class="sxs-lookup"><span data-stu-id="83118-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="83118-218">Kierunek jest do miasta lub poza miastem</span><span class="sxs-lookup"><span data-stu-id="83118-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="83118-219">W poniższej tabeli przedstawiono kombinacje wartości wejściowych i mnożnik cen szczytowych:</span><span class="sxs-lookup"><span data-stu-id="83118-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="83118-220">Day</span><span class="sxs-lookup"><span data-stu-id="83118-220">Day</span></span>        | <span data-ttu-id="83118-221">Time</span><span class="sxs-lookup"><span data-stu-id="83118-221">Time</span></span>         | <span data-ttu-id="83118-222">Kierunek</span><span class="sxs-lookup"><span data-stu-id="83118-222">Direction</span></span> | <span data-ttu-id="83118-223">Premium</span><span class="sxs-lookup"><span data-stu-id="83118-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="83118-224">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-224">Weekday</span></span>    | <span data-ttu-id="83118-225">poranny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-225">morning rush</span></span> | <span data-ttu-id="83118-226">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-226">inbound</span></span>   | <span data-ttu-id="83118-227">x 2.00</span><span class="sxs-lookup"><span data-stu-id="83118-227">x 2.00</span></span>  |
| <span data-ttu-id="83118-228">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-228">Weekday</span></span>    | <span data-ttu-id="83118-229">poranny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-229">morning rush</span></span> | <span data-ttu-id="83118-230">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-230">outbound</span></span>  | <span data-ttu-id="83118-231">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-231">x 1.00</span></span>  |
| <span data-ttu-id="83118-232">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-232">Weekday</span></span>    | <span data-ttu-id="83118-233">Dzień</span><span class="sxs-lookup"><span data-stu-id="83118-233">daytime</span></span>      | <span data-ttu-id="83118-234">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-234">inbound</span></span>   | <span data-ttu-id="83118-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="83118-235">x 1.50</span></span>  |
| <span data-ttu-id="83118-236">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-236">Weekday</span></span>    | <span data-ttu-id="83118-237">Dzień</span><span class="sxs-lookup"><span data-stu-id="83118-237">daytime</span></span>      | <span data-ttu-id="83118-238">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-238">outbound</span></span>  | <span data-ttu-id="83118-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="83118-239">x 1.50</span></span>  |
| <span data-ttu-id="83118-240">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-240">Weekday</span></span>    | <span data-ttu-id="83118-241">wieczorny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-241">evening rush</span></span> | <span data-ttu-id="83118-242">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-242">inbound</span></span>   | <span data-ttu-id="83118-243">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-243">x 1.00</span></span>  |
| <span data-ttu-id="83118-244">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-244">Weekday</span></span>    | <span data-ttu-id="83118-245">wieczorny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-245">evening rush</span></span> | <span data-ttu-id="83118-246">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-246">outbound</span></span>  | <span data-ttu-id="83118-247">x 2.00</span><span class="sxs-lookup"><span data-stu-id="83118-247">x 2.00</span></span>  |
| <span data-ttu-id="83118-248">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-248">Weekday</span></span>    | <span data-ttu-id="83118-249">Noc</span><span class="sxs-lookup"><span data-stu-id="83118-249">overnight</span></span>    | <span data-ttu-id="83118-250">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-250">inbound</span></span>   | <span data-ttu-id="83118-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="83118-251">x 0.75</span></span>  |
| <span data-ttu-id="83118-252">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="83118-252">Weekday</span></span>    | <span data-ttu-id="83118-253">Noc</span><span class="sxs-lookup"><span data-stu-id="83118-253">overnight</span></span>    | <span data-ttu-id="83118-254">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-254">outbound</span></span>  | <span data-ttu-id="83118-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="83118-255">x 0.75</span></span>  |
| <span data-ttu-id="83118-256">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-256">Weekend</span></span>    | <span data-ttu-id="83118-257">poranny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-257">morning rush</span></span> | <span data-ttu-id="83118-258">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-258">inbound</span></span>   | <span data-ttu-id="83118-259">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-259">x 1.00</span></span>  |
| <span data-ttu-id="83118-260">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-260">Weekend</span></span>    | <span data-ttu-id="83118-261">poranny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-261">morning rush</span></span> | <span data-ttu-id="83118-262">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-262">outbound</span></span>  | <span data-ttu-id="83118-263">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-263">x 1.00</span></span>  |
| <span data-ttu-id="83118-264">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-264">Weekend</span></span>    | <span data-ttu-id="83118-265">Dzień</span><span class="sxs-lookup"><span data-stu-id="83118-265">daytime</span></span>      | <span data-ttu-id="83118-266">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-266">inbound</span></span>   | <span data-ttu-id="83118-267">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-267">x 1.00</span></span>  |
| <span data-ttu-id="83118-268">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-268">Weekend</span></span>    | <span data-ttu-id="83118-269">Dzień</span><span class="sxs-lookup"><span data-stu-id="83118-269">daytime</span></span>      | <span data-ttu-id="83118-270">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-270">outbound</span></span>  | <span data-ttu-id="83118-271">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-271">x 1.00</span></span>  |
| <span data-ttu-id="83118-272">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-272">Weekend</span></span>    | <span data-ttu-id="83118-273">wieczorny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-273">evening rush</span></span> | <span data-ttu-id="83118-274">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-274">inbound</span></span>   | <span data-ttu-id="83118-275">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-275">x 1.00</span></span>  |
| <span data-ttu-id="83118-276">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-276">Weekend</span></span>    | <span data-ttu-id="83118-277">wieczorny pośpiech</span><span class="sxs-lookup"><span data-stu-id="83118-277">evening rush</span></span> | <span data-ttu-id="83118-278">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-278">outbound</span></span>  | <span data-ttu-id="83118-279">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-279">x 1.00</span></span>  |
| <span data-ttu-id="83118-280">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-280">Weekend</span></span>    | <span data-ttu-id="83118-281">Noc</span><span class="sxs-lookup"><span data-stu-id="83118-281">overnight</span></span>    | <span data-ttu-id="83118-282">przychodzące</span><span class="sxs-lookup"><span data-stu-id="83118-282">inbound</span></span>   | <span data-ttu-id="83118-283">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-283">x 1.00</span></span>  |
| <span data-ttu-id="83118-284">Weekend</span><span class="sxs-lookup"><span data-stu-id="83118-284">Weekend</span></span>    | <span data-ttu-id="83118-285">Noc</span><span class="sxs-lookup"><span data-stu-id="83118-285">overnight</span></span>    | <span data-ttu-id="83118-286">Wychodzących</span><span class="sxs-lookup"><span data-stu-id="83118-286">outbound</span></span>  | <span data-ttu-id="83118-287">x 1.00</span><span class="sxs-lookup"><span data-stu-id="83118-287">x 1.00</span></span>  |

<span data-ttu-id="83118-288">Istnieje 16 różnych kombinacji trzech zmiennych.</span><span class="sxs-lookup"><span data-stu-id="83118-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="83118-289">Łącząc niektóre warunki, uprościsz wyrażenie przełącznika końcowego.</span><span class="sxs-lookup"><span data-stu-id="83118-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="83118-290">System, który pobiera opłaty za <xref:System.DateTime> przejazd, wykorzystuje strukturę w momencie pobrania opłaty drogowej.</span><span class="sxs-lookup"><span data-stu-id="83118-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="83118-291">Tworzenie metod członkowskich, które tworzą zmienne z poprzedniej tabeli.</span><span class="sxs-lookup"><span data-stu-id="83118-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="83118-292">Następująca funkcja używa wyrażenia przełącznika pasującego do wzorca, <xref:System.DateTime> aby wyrazić, czy reprezentuje weekend, czy dzień tygodnia:</span><span class="sxs-lookup"><span data-stu-id="83118-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="83118-293">Ta metoda działa, ale jest powtarzalna.</span><span class="sxs-lookup"><span data-stu-id="83118-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="83118-294">Można go uprościć, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="83118-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="83118-295">Następnie dodaj podobną funkcję, aby kategoryzować czas do bloków:</span><span class="sxs-lookup"><span data-stu-id="83118-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="83118-296">Poprzednia metoda nie używa dopasowania wzorca.</span><span class="sxs-lookup"><span data-stu-id="83118-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="83118-297">Jest to jaśniejsze przy użyciu `if` znanej kaskady stwierdzeń.</span><span class="sxs-lookup"><span data-stu-id="83118-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="83118-298">Aby przekonwertować `enum` każdy zakres czasu na wartość dyskretną, należy dodać wartość prywatną.</span><span class="sxs-lookup"><span data-stu-id="83118-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="83118-299">Po utworzeniu tych metod można `switch` użyć innego wyrażenia ze **wzorcem krotki** do obliczania premii cenowej.</span><span class="sxs-lookup"><span data-stu-id="83118-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="83118-300">Można zbudować `switch` wyrażenie z wszystkich 16 broni:</span><span class="sxs-lookup"><span data-stu-id="83118-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="83118-301">Powyższy kod działa, ale można go uprościć.</span><span class="sxs-lookup"><span data-stu-id="83118-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="83118-302">Wszystkie osiem kombinacji na weekend ma taką samą opłatę.</span><span class="sxs-lookup"><span data-stu-id="83118-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="83118-303">Możesz zastąpić wszystkie osiem następującym wierszem:</span><span class="sxs-lookup"><span data-stu-id="83118-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="83118-304">Ruch przychodzący i wychodzący mają ten sam mnożnik w ciągu dnia w dni powszednie i w godzinach nocnych.</span><span class="sxs-lookup"><span data-stu-id="83118-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="83118-305">Te cztery ramiona przełącznika można zastąpić następującymi dwiema liniami:</span><span class="sxs-lookup"><span data-stu-id="83118-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="83118-306">Kod powinien wyglądać jak następujący kod po tych dwóch zmianach:</span><span class="sxs-lookup"><span data-stu-id="83118-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="83118-307">Na koniec możesz usunąć dwa godziny szczytu, które płacą normalną cenę.</span><span class="sxs-lookup"><span data-stu-id="83118-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="83118-308">Po usunięciu tych ramion można `false` zastąpić je`_`odrzutem ( ) w ostatnim ramieniu przełącznika.</span><span class="sxs-lookup"><span data-stu-id="83118-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="83118-309">Będziesz mieć następującą gotową metodę:</span><span class="sxs-lookup"><span data-stu-id="83118-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="83118-310">W tym przykładzie wyróżniono jedną z zalet dopasowywania wzorców: gałęzie wzorca są oceniane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="83118-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="83118-311">Jeśli zmienisz ich tak, że wcześniejsza gałąź obsługuje jeden z późniejszych przypadków, kompilator ostrzega o nieosiągalny kod.</span><span class="sxs-lookup"><span data-stu-id="83118-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="83118-312">Te reguły języka ułatwiły wykonanie poprzednich uproszczeń z pewnością, że kod się nie zmienił.</span><span class="sxs-lookup"><span data-stu-id="83118-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="83118-313">Dopasowywanie wzorców sprawia, że niektóre typy kodu są bardziej czytelne i oferują alternatywę dla technik obiektowych, gdy nie można dodać kodu do klas.</span><span class="sxs-lookup"><span data-stu-id="83118-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="83118-314">Chmura powoduje, że dane i funkcje są rozstawione.</span><span class="sxs-lookup"><span data-stu-id="83118-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="83118-315">*Kształt* danych i *operacje* na nim nie muszą być opisane razem.</span><span class="sxs-lookup"><span data-stu-id="83118-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="83118-316">W tym samouczku zużyłeś istniejące dane w zupełnie inny sposób niż jego oryginalna funkcja.</span><span class="sxs-lookup"><span data-stu-id="83118-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="83118-317">Dopasowanie wzorca dało możliwość pisania funkcji, które overrode tych typów, nawet jeśli nie można rozszerzyć je.</span><span class="sxs-lookup"><span data-stu-id="83118-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="83118-318">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="83118-318">Next steps</span></span>

<span data-ttu-id="83118-319">Gotowy kod można pobrać z repozytorium GitHub [dotnet/samples.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished)</span><span class="sxs-lookup"><span data-stu-id="83118-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="83118-320">Eksploruj wzorce samodzielnie i dodaj tę technikę do swoich regularnych działań związanych z kodowaniem.</span><span class="sxs-lookup"><span data-stu-id="83118-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="83118-321">Nauka tych technik daje inny sposób podejścia do problemów i tworzenia nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="83118-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
