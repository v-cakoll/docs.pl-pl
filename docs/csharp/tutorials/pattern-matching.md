---
title: Użyj funkcji dopasowywania wzorca, aby rozszerzyć typy danych
description: W tym samouczku zaawansowane pokazuje, jak tworzyć funkcje przy użyciu danych i algorytmy, które są tworzone oddzielnie za pomocą metod dopasowania do wzorca.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 210cb15699057482e36984f80dd08f8b19db55d3
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58051545"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="099d4-103">Samouczek: Aby rozszerzyć typy danych przy użyciu funkcji dopasowywania wzorca</span><span class="sxs-lookup"><span data-stu-id="099d4-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="099d4-104">C#7 wprowadzono podstawowy wzorzec dopasowywania funkcji.</span><span class="sxs-lookup"><span data-stu-id="099d4-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="099d4-105">Te funkcje zostały rozszerzone w C# 8 za pomocą nowego wyrażenia i wzorce.</span><span class="sxs-lookup"><span data-stu-id="099d4-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="099d4-106">Można napisać funkcji, który zachowuje się tak, jakby rozszerzone typy, które mogą być w innych bibliotekach.</span><span class="sxs-lookup"><span data-stu-id="099d4-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="099d4-107">Innym zastosowaniem wzorców jest tworzenie funkcji wymaganych przez aplikację, która nie jest podstawową cechą typ zostanie przedłużony.</span><span class="sxs-lookup"><span data-stu-id="099d4-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="099d4-108">W tym samouczku dowiesz się, jak:</span><span class="sxs-lookup"><span data-stu-id="099d4-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="099d4-109">Jak rozpoznać sytuacji, w którym dopasowywania do wzorca powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="099d4-109">How to recognize situations where pattern matching should be used.</span></span>
> * <span data-ttu-id="099d4-110">Jak zaimplementować zachowanie na podstawie typu i wartości właściwości za pomocą wyrażeniach dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="099d4-110">How to use pattern matching expressions to implement behavior based on types and property values.</span></span>
> * <span data-ttu-id="099d4-111">Jak połączyć dopasowania z innymi technikami, aby utworzyć pełną algorytmów do wzorca.</span><span class="sxs-lookup"><span data-stu-id="099d4-111">How to combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="099d4-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="099d4-112">Prerequisites</span></span>

<span data-ttu-id="099d4-113">Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="099d4-113">You'll need to set up your machine to run .NET Core, including the C# 8.0 preview compiler.</span></span> <span data-ttu-id="099d4-114">C# 8 kompilatora w wersji zapoznawczej jest dostępna przy użyciu najnowszej [2019 usługi Visual Studio w wersji zapoznawczej](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), lub r [.NET Core 3.0 w wersji zapoznawczej](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="099d4-114">The C# 8 preview compiler is available with the latest [Visual Studio 2019 preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="099d4-115">W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="099d4-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="099d4-116">Scenariusze dotyczące dopasowywania do wzorca</span><span class="sxs-lookup"><span data-stu-id="099d4-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="099d4-117">Nowoczesne tworzenie oprogramowania często obejmuje integrowanie danych z wielu źródeł i prezentowanie informacji i szczegółowe informacje na podstawie tych danych w jednej aplikacji cohesive.</span><span class="sxs-lookup"><span data-stu-id="099d4-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="099d4-118">Ty i Twój zespół nie będzie miał formant lub uzyskania dostępu do wszystkich typów, które reprezentują dane przychodzące.</span><span class="sxs-lookup"><span data-stu-id="099d4-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="099d4-119">Klasyczne projektowanie zorientowane obiektowo wywoływałby do tworzenia typów w aplikacji, który reprezentuje każdego typu danych te dane z wielu źródeł.</span><span class="sxs-lookup"><span data-stu-id="099d4-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="099d4-120">Następnie aplikacja będzie pracować z tych nowych typów, tworzenie hierarchii dziedziczenia, tworzenie metod wirtualnych i zaimplementować abstrakcje.</span><span class="sxs-lookup"><span data-stu-id="099d4-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="099d4-121">Techniki te działają i czasami są najlepsze narzędzia.</span><span class="sxs-lookup"><span data-stu-id="099d4-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="099d4-122">Czasami można napisać mniejszej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="099d4-122">Other times you can write less code.</span></span> <span data-ttu-id="099d4-123">Można napisać więcej zwykłego kodu przy użyciu technik, które rozdziela się dane przed operacjami, które manipulowania tych danych.</span><span class="sxs-lookup"><span data-stu-id="099d4-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="099d4-124">W tym samouczku utworzysz i zapoznaj się z aplikacji, która przyjmuje dane przychodzące z kilku źródeł zewnętrznych dla jednego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="099d4-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="099d4-125">Zobaczysz jak **dopasowywania do wzorca** umożliwia wydajne wykorzystanie i przetworzyć te dane w sposób, który nie był części systemu, oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="099d4-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="099d4-126">Należy wziąć pod uwagę głównych Miasto używanej drogi i ceny godziny szczytu do zarządzania ruchem.</span><span class="sxs-lookup"><span data-stu-id="099d4-126">Consider a major metro area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="099d4-127">Możesz napisać aplikację, który oblicza drogi pojazdu na podstawie jego typu.</span><span class="sxs-lookup"><span data-stu-id="099d4-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="099d4-128">Ulepszenia nowsze dołączania, cen, na podstawie liczby użytkowników w pojeździe.</span><span class="sxs-lookup"><span data-stu-id="099d4-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="099d4-129">Dalsze udoskonalenia dodać, ceny, oparte na godzinę i dzień tygodnia.</span><span class="sxs-lookup"><span data-stu-id="099d4-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="099d4-130">Z tego krótkiego opisu może mieć szybko ustalonej hierarchię obiektów do modelu tego systemu.</span><span class="sxs-lookup"><span data-stu-id="099d4-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="099d4-131">Jednak danych pochodzi z wielu źródeł, takich jak inne systemy zarządzania rejestracji vehicle.</span><span class="sxs-lookup"><span data-stu-id="099d4-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="099d4-132">Te systemy Podaj różnych klas do modelu danych, a nie masz modelu pojedynczy obiekt, w których można użyć.</span><span class="sxs-lookup"><span data-stu-id="099d4-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="099d4-133">W tym samouczku użyjesz tych klas uproszczona do modelu danych pojazdu z systemów zewnętrznych, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="099d4-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](../../../samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="099d4-134">Możesz pobrać kod początkowy, od [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="099d4-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="099d4-135">Widać klasy pojazdu pochodzą z różnych systemów i znajdują się w różnych obszarach nazw.</span><span class="sxs-lookup"><span data-stu-id="099d4-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="099d4-136">Nie wspólnej bazy klasy innej niż `System.Object` nadającego się.</span><span class="sxs-lookup"><span data-stu-id="099d4-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="099d4-137">Wzorzec dopasowania projektów</span><span class="sxs-lookup"><span data-stu-id="099d4-137">Pattern matching designs</span></span>

<span data-ttu-id="099d4-138">Scenariusz, w tym samouczku używane są wyróżnione rodzaje problemów, które są odpowiednie na potrzeby dopasowywania do wzorca rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="099d4-138">The scenario used in this tutorial highlights the kinds of problems that are well suited to use pattern matching to solve:</span></span> 

- <span data-ttu-id="099d4-139">Obiekty, które są potrzebne do pracy z nie występują w hierarchię obiektów, która pasuje do określonych celów.</span><span class="sxs-lookup"><span data-stu-id="099d4-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="099d4-140">Możliwe, że pracujesz z klasami, które są częścią niepowiązanych systemów.</span><span class="sxs-lookup"><span data-stu-id="099d4-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="099d4-141">Funkcje, które dodajesz nie jest częścią abstrakcji core dla tych klas.</span><span class="sxs-lookup"><span data-stu-id="099d4-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="099d4-142">Płatny sposób zapłaty pojazdu *zmiany* dla różnych typów pojazdów, ale płatny nie jest podstawowa funkcja pojazdu.</span><span class="sxs-lookup"><span data-stu-id="099d4-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="099d4-143">Gdy *kształt* danych i *operacji* na tym dane nie zostały opisane razem, funkcje dopasowania wzorca C# ułatwienia pracy z.</span><span class="sxs-lookup"><span data-stu-id="099d4-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span> 

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="099d4-144">Implementowanie obliczeń płatny podstawowe</span><span class="sxs-lookup"><span data-stu-id="099d4-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="099d4-145">Najbardziej podstawowa obliczeń płatny opiera się tylko pod względem typu pojazdów:</span><span class="sxs-lookup"><span data-stu-id="099d4-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="099d4-146">Element `Car` jest $2.00.</span><span class="sxs-lookup"><span data-stu-id="099d4-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="099d4-147">Element `Taxi` jest 3.50 $.</span><span class="sxs-lookup"><span data-stu-id="099d4-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="099d4-148">Element `Bus` jest 5,00 zł.</span><span class="sxs-lookup"><span data-stu-id="099d4-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="099d4-149">Element `DeliveryTruck` jest 10,00 zł</span><span class="sxs-lookup"><span data-stu-id="099d4-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="099d4-150">Utwórz nową `TollCalculator` klasy i implementuje dopasowania do wzorca w pojeździe można pobrać kwota opłaty.</span><span class="sxs-lookup"><span data-stu-id="099d4-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span>

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
            Car c => 2.00m,
            Taxi t => 3.50m,
            Bus b => 5.00m,
            DeliveryTruck t => 10.00m,
            { } => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="099d4-151">W poprzednim kodzie użyto **wyrażenie switch** (nie taka sama, jak [ `switch` ](../language-reference/keywords/switch.md) instrukcji), które testują **wpisz wzór**.</span><span class="sxs-lookup"><span data-stu-id="099d4-151">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="099d4-152">A **wyrażenie switch** rozpoczyna się od zmiennej, `vehicle` w poprzednim kodzie, a następnie `switch` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="099d4-152">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="099d4-153">Następnie nadchodzi arms przełącznika umieszczone w nawiasach klamrowych.</span><span class="sxs-lookup"><span data-stu-id="099d4-153">Next comes all the switch arms inside curly braces.</span></span> <span data-ttu-id="099d4-154">`switch` Wyrażenie sprawia, że pozostałe elementy składni, która otacza `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="099d4-154">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="099d4-155">`case` — Słowo kluczowe zostanie pominięty, a wynik każdego arm jest wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="099d4-155">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="099d4-156">Ostatnie dwa arms wyświetlenie nowej funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="099d4-156">The last two arms show a new language feature.</span></span> <span data-ttu-id="099d4-157">`{ }` Przypadek pasuje do dowolnego obiektu inną niż null, który nie pasuje do wcześniejszych arm.</span><span class="sxs-lookup"><span data-stu-id="099d4-157">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="099d4-158">Ta arm połowy wszelkie nieprawidłowe typy przekazane do tej metody.</span><span class="sxs-lookup"><span data-stu-id="099d4-158">This arm catches any incorrect types passed to this method.</span></span> <span data-ttu-id="099d4-159">Na koniec `null` przechwytuje wzorca, gdy `null` jest przekazywany do tej metody.</span><span class="sxs-lookup"><span data-stu-id="099d4-159">Finally, the `null` pattern catches when `null` is passed to this method.</span></span> <span data-ttu-id="099d4-160">`null` Wzorzec może być ostatnie, ponieważ inne wzorce typ zgodny tylko obiektów innych niż null poprawnego typu.</span><span class="sxs-lookup"><span data-stu-id="099d4-160">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="099d4-161">Możesz przetestować ten kod, używając następującego kodu w `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="099d4-161">You can test this code using the following code in `Program.cs`:</span></span>

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
                Console.WriteLine("Caught an argument exception when using the wrong type", DayOfWeek.Friday);
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

<span data-ttu-id="099d4-162">Ten kod znajduje się projekt startowy, ale są oznaczone jako komentarz. Usuń komentarze i można przetestować zostały zapisane.</span><span class="sxs-lookup"><span data-stu-id="099d4-162">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="099d4-163">Trwa uruchamianie zobaczyć, jak wzorce mogą pomóc tworzyć algorytmów, której kod i dane są niezależne.</span><span class="sxs-lookup"><span data-stu-id="099d4-163">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="099d4-164">`switch` Wyrażenie sprawdza typ i tworzy różne wartości, w oparciu o wyniki.</span><span class="sxs-lookup"><span data-stu-id="099d4-164">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="099d4-165">To dopiero początek.</span><span class="sxs-lookup"><span data-stu-id="099d4-165">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="099d4-166">Dodaj rozszerzenia ceny</span><span class="sxs-lookup"><span data-stu-id="099d4-166">Add occupancy pricing</span></span>

<span data-ttu-id="099d4-167">Urząd płatny chce, aby zachęcić pojazdów przechodzić z maksymalną wydajnością.</span><span class="sxs-lookup"><span data-stu-id="099d4-167">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="099d4-168">Decydujesz się one do bardziej pojazdów mają mniejszą liczbę osób, gdy zachęcać pojazdów pełną, udostępniając niższe ceny:</span><span class="sxs-lookup"><span data-stu-id="099d4-168">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="099d4-169">Samochodów i taksówek za pomocą pasażerowie nie zapłacić dodatkowy 0,50 USD.</span><span class="sxs-lookup"><span data-stu-id="099d4-169">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="099d4-170">Uzyskaj rabat w wysokości 0,50, samochodów i taksówek za pomocą dwóch pasażerów.</span><span class="sxs-lookup"><span data-stu-id="099d4-170">Cars and taxis with two passengers get a 0.50 discount.</span></span>
- <span data-ttu-id="099d4-171">Uzyskaj Rabat $1.00, samochodów i taksówek za pomocą trzech lub więcej osób.</span><span class="sxs-lookup"><span data-stu-id="099d4-171">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="099d4-172">Autobusów, które są mniej niż 50% zapełnienia zapłacić dodatkowy $2.00.</span><span class="sxs-lookup"><span data-stu-id="099d4-172">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="099d4-173">Autobusów, które są ponad 90% zapełnienia uzyskać rabat $1.00.</span><span class="sxs-lookup"><span data-stu-id="099d4-173">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="099d4-174">Te reguły można zaimplementować przy użyciu **wzorzec właściwość** w tym samym wyrażenie switch.</span><span class="sxs-lookup"><span data-stu-id="099d4-174">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="099d4-175">Wzorzec właściwość sprawdza, czy właściwości obiektu po określeniu typu.</span><span class="sxs-lookup"><span data-stu-id="099d4-175">The property pattern examines properties of the object once the type has been determined.</span></span>  <span data-ttu-id="099d4-176">W przypadku pojedynczego `Car` rozwija do czterech różnych przypadków:</span><span class="sxs-lookup"><span data-stu-id="099d4-176">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0} => 2.00m + 0.50m,
    Car { Passengers: 1 } => 2.0m,
    Car { Passengers: 2} => 2.0m - 0.50m,
    Car c when c.Passengers > 2 => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="099d4-177">Pierwsze trzy przypadki testów typ jako `Car`, następnie sprawdź wartość `Passengers` właściwości.</span><span class="sxs-lookup"><span data-stu-id="099d4-177">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="099d4-178">Jeśli obie są zgodne, to wyrażenie jest oceniana i zwracana.</span><span class="sxs-lookup"><span data-stu-id="099d4-178">If both match, that expression is evaluated and returned.</span></span> <span data-ttu-id="099d4-179">Pokazuje końcowego klauzuli `when` klauzula dla wzorca właściwości.</span><span class="sxs-lookup"><span data-stu-id="099d4-179">The final clause shows the `when` clause for a property pattern.</span></span> <span data-ttu-id="099d4-180">Możesz użyć `when` klauzulę, aby przetestować warunki niż równość dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="099d4-180">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="099d4-181">W powyższym przykładzie `when` klauzuli testy, aby zobaczyć, że są więcej niż 2 pasażerów w samochodu.</span><span class="sxs-lookup"><span data-stu-id="099d4-181">In the preceding example, the `when` clause tests to see that there are more than 2 passengers in the car.</span></span> <span data-ttu-id="099d4-182">Ściśle rzecz ujmując nie jest konieczne, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="099d4-182">Strictly speaking, it's not necessary in this example.</span></span>

<span data-ttu-id="099d4-183">Może także zwiększyć przypadków dla taksówek w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="099d4-183">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0} => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2} => 3.50m - 0.50m,
    Taxi t => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="099d4-184">W powyższym przykładzie `when` na ostatnim przypadku pominięcia klauzuli.</span><span class="sxs-lookup"><span data-stu-id="099d4-184">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="099d4-185">Następnie należy zaimplementować reguły zajętość rozwijając przypadków autobusów, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="099d4-185">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following exmaple:</span></span>

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

<span data-ttu-id="099d4-186">Urząd płatny nie jest związana z liczby pasażerów ciężarówek dostarczania.</span><span class="sxs-lookup"><span data-stu-id="099d4-186">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="099d4-187">Zamiast tego są opłaty za bardziej oparte na klasę wagi ciężarówek.</span><span class="sxs-lookup"><span data-stu-id="099d4-187">Instead, they charge more based on the weight class of the trucks.</span></span> <span data-ttu-id="099d4-188">Ciężarówek ponad 5000 modułów równoważenia obciążenia jest naliczana dodatkowa 5.00 $.</span><span class="sxs-lookup"><span data-stu-id="099d4-188">Trucks over 5000 lbs are charged an extra $5.00.</span></span> <span data-ttu-id="099d4-189">Ciężarówek światła, w obszarze 3000 lbs otrzymują rabat w wysokości $2.00.</span><span class="sxs-lookup"><span data-stu-id="099d4-189">Light trucks, under 3000 lbs are given a $2.00 discount.</span></span>  <span data-ttu-id="099d4-190">Tej reguły jest implementowane za pomocą następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="099d4-190">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="099d4-191">Gdy wszystko będzie gotowe, będziesz mieć na metodę, która wygląda podobnie do następujących:</span><span class="sxs-lookup"><span data-stu-id="099d4-191">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0} => 2.00m + 0.50m,
    Car { Passengers: 1 } => 2.0m,
    Car { Passengers: 2} => 2.0m - 0.50m,
    Car c when c.Passengers > 2 => 2.00m - 1.0m,
   
    Taxi { Fares: 0} => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2} => 3.50m - 0.50m,
    Taxi t => 3.50m - 1.00m,
    
    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m, 
    Bus b => 5.00m,
    
    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

## <a name="recursive-patterns"></a><span data-ttu-id="099d4-192">Wzorce cykliczne</span><span class="sxs-lookup"><span data-stu-id="099d4-192">Recursive patterns</span></span>

<span data-ttu-id="099d4-193">Aby włączyć ten kod mniej powtarzających się przy użyciu **wzorców cyklicznego**.</span><span class="sxs-lookup"><span data-stu-id="099d4-193">You can make this code less repetitive by using **recursive patterns**.</span></span> <span data-ttu-id="099d4-194">`Car` i `Taxi` mają czterech różnych arms w powyższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="099d4-194">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="099d4-195">W obu przypadkach można utworzyć wzorzec typ, który trafiają do wzorca właściwości.</span><span class="sxs-lookup"><span data-stu-id="099d4-195">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="099d4-196">W poniższym kodzie pokazano tej techniki:</span><span class="sxs-lookup"><span data-stu-id="099d4-196">This technique is shown in the following code:</span></span>

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
        { } => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="099d4-197">W poprzednim przykładzie, za pomocą wyrażenia cyklicznego oznacza, że nie powtarzaj `Car` i `Taxi` arms zawierają arms podrzędne, które testują wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="099d4-197">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms contain child arms that test the property value.</span></span> <span data-ttu-id="099d4-198">Ta technika nie jest używany dla `Bus` i `DeliveryTruck` aktywacji, ponieważ te arms testujesz zakresów dla właściwości wartości dyskretnych nie.</span><span class="sxs-lookup"><span data-stu-id="099d4-198">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="099d4-199">Dodaj ceny szczytowa</span><span class="sxs-lookup"><span data-stu-id="099d4-199">Add peak pricing</span></span>

<span data-ttu-id="099d4-200">Dla funkcji końcowego urząd płatny chce dodać ceny szczytowa poufnych czasowo.</span><span class="sxs-lookup"><span data-stu-id="099d4-200">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="099d4-201">Podczas rano i wieczorem łazienkowych godzin zostaną podwojone drogi.</span><span class="sxs-lookup"><span data-stu-id="099d4-201">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="099d4-202">Tej reguły ma wpływ tylko na ruch sieciowy w jeden kierunek: przychodzący do miasta rano i wychodzących w ciągu godziny łazienkowych wieczór.</span><span class="sxs-lookup"><span data-stu-id="099d4-202">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="099d4-203">W innych przypadkach w pracy drogi Zwiększ o 50%.</span><span class="sxs-lookup"><span data-stu-id="099d4-203">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="099d4-204">Godziny nocne i wcześnie rano, drogi zostały zredukowane przez 25%.</span><span class="sxs-lookup"><span data-stu-id="099d4-204">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="099d4-205">Weekend jest normalną szybkość, niezależnie od tego, w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="099d4-205">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="099d4-206">Użyjesz dopasowywania do wzorca dla tej funkcji, ale będzie zintegrować ją z innymi technikami.</span><span class="sxs-lookup"><span data-stu-id="099d4-206">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="099d4-207">Można utworzyć wyrażenie dopasowania do wzorca pojedynczej będzie konta wszystkie kombinacje kierunku, dnia tygodnia i godzinę.</span><span class="sxs-lookup"><span data-stu-id="099d4-207">You could build a single pattern match expression that would account all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="099d4-208">Wynik byłby skomplikowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="099d4-208">The result would be a complicated expression.</span></span> <span data-ttu-id="099d4-209">Jest trudny do odczytania i trudne do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="099d4-209">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="099d4-210">Które czyni go trudno sprawdzić ich poprawność.</span><span class="sxs-lookup"><span data-stu-id="099d4-210">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="099d4-211">Zamiast tego należy połączyć te metody do tworzenia krotki wartości, która zwięźle opisuje te stany.</span><span class="sxs-lookup"><span data-stu-id="099d4-211">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="099d4-212">Następnie użyj dopasowywania wzorców do obliczania mnożnik dla płatny.</span><span class="sxs-lookup"><span data-stu-id="099d4-212">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="099d4-213">Spójna kolekcja znajdująca się zawiera trzy osobne warunki:</span><span class="sxs-lookup"><span data-stu-id="099d4-213">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="099d4-214">Dzień jest dniem powszednim lub weekendy.</span><span class="sxs-lookup"><span data-stu-id="099d4-214">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="099d4-215">Pasmo czas, kiedy są zbierane płatny.</span><span class="sxs-lookup"><span data-stu-id="099d4-215">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="099d4-216">Kierunek to miasto lub miejscowość</span><span class="sxs-lookup"><span data-stu-id="099d4-216">The direction is into the city or out of the city</span></span>

<span data-ttu-id="099d4-217">W poniższej tabeli przedstawiono kombinacje wartości wejściowe i ze szczytową, cennik mnożnik:</span><span class="sxs-lookup"><span data-stu-id="099d4-217">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="099d4-218">Dzień</span><span class="sxs-lookup"><span data-stu-id="099d4-218">Day</span></span>        | <span data-ttu-id="099d4-219">Godzina</span><span class="sxs-lookup"><span data-stu-id="099d4-219">Time</span></span>         | <span data-ttu-id="099d4-220">Kierunek</span><span class="sxs-lookup"><span data-stu-id="099d4-220">Direction</span></span> | <span data-ttu-id="099d4-221">Premium</span><span class="sxs-lookup"><span data-stu-id="099d4-221">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="099d4-222">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-222">Weekday</span></span>    | <span data-ttu-id="099d4-223">łazienkowych rano</span><span class="sxs-lookup"><span data-stu-id="099d4-223">morning rush</span></span> | <span data-ttu-id="099d4-224">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-224">inbound</span></span>   | <span data-ttu-id="099d4-225">x 2.00</span><span class="sxs-lookup"><span data-stu-id="099d4-225">x 2.00</span></span>  |
| <span data-ttu-id="099d4-226">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-226">Weekday</span></span>    | <span data-ttu-id="099d4-227">łazienkowych rano</span><span class="sxs-lookup"><span data-stu-id="099d4-227">morning rush</span></span> | <span data-ttu-id="099d4-228">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-228">outbound</span></span>  | <span data-ttu-id="099d4-229">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-229">x 1.00</span></span>  |
| <span data-ttu-id="099d4-230">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-230">Weekday</span></span>    | <span data-ttu-id="099d4-231">za dnia</span><span class="sxs-lookup"><span data-stu-id="099d4-231">daytime</span></span>      | <span data-ttu-id="099d4-232">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-232">inbound</span></span>   | <span data-ttu-id="099d4-233">x 1.50</span><span class="sxs-lookup"><span data-stu-id="099d4-233">x 1.50</span></span>  |
| <span data-ttu-id="099d4-234">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-234">Weekday</span></span>    | <span data-ttu-id="099d4-235">za dnia</span><span class="sxs-lookup"><span data-stu-id="099d4-235">daytime</span></span>      | <span data-ttu-id="099d4-236">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-236">outbound</span></span>  | <span data-ttu-id="099d4-237">x 1.50</span><span class="sxs-lookup"><span data-stu-id="099d4-237">x 1.50</span></span>  |
| <span data-ttu-id="099d4-238">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-238">Weekday</span></span>    | <span data-ttu-id="099d4-239">łazienkowych wieczorem</span><span class="sxs-lookup"><span data-stu-id="099d4-239">evening rush</span></span> | <span data-ttu-id="099d4-240">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-240">inbound</span></span>   | <span data-ttu-id="099d4-241">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-241">x 1.00</span></span>  |
| <span data-ttu-id="099d4-242">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-242">Weekday</span></span>    | <span data-ttu-id="099d4-243">łazienkowych wieczorem</span><span class="sxs-lookup"><span data-stu-id="099d4-243">evening rush</span></span> | <span data-ttu-id="099d4-244">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-244">outbound</span></span>  | <span data-ttu-id="099d4-245">x 2.00</span><span class="sxs-lookup"><span data-stu-id="099d4-245">x 2.00</span></span>  |
| <span data-ttu-id="099d4-246">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-246">Weekday</span></span>    | <span data-ttu-id="099d4-247">procesu na noc</span><span class="sxs-lookup"><span data-stu-id="099d4-247">overnight</span></span>    | <span data-ttu-id="099d4-248">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-248">inbound</span></span>   | <span data-ttu-id="099d4-249">x wartość 0,75</span><span class="sxs-lookup"><span data-stu-id="099d4-249">x 0.75</span></span>  |
| <span data-ttu-id="099d4-250">Dzień tygodnia</span><span class="sxs-lookup"><span data-stu-id="099d4-250">Weekday</span></span>    | <span data-ttu-id="099d4-251">procesu na noc</span><span class="sxs-lookup"><span data-stu-id="099d4-251">overnight</span></span>    | <span data-ttu-id="099d4-252">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-252">outbound</span></span>  | <span data-ttu-id="099d4-253">x wartość 0,75</span><span class="sxs-lookup"><span data-stu-id="099d4-253">x 0.75</span></span>  |
| <span data-ttu-id="099d4-254">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-254">Weekend</span></span>    | <span data-ttu-id="099d4-255">łazienkowych rano</span><span class="sxs-lookup"><span data-stu-id="099d4-255">morning rush</span></span> | <span data-ttu-id="099d4-256">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-256">inbound</span></span>   | <span data-ttu-id="099d4-257">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-257">x 1.00</span></span>  |
| <span data-ttu-id="099d4-258">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-258">Weekend</span></span>    | <span data-ttu-id="099d4-259">łazienkowych rano</span><span class="sxs-lookup"><span data-stu-id="099d4-259">morning rush</span></span> | <span data-ttu-id="099d4-260">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-260">outbound</span></span>  | <span data-ttu-id="099d4-261">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-261">x 1.00</span></span>  |
| <span data-ttu-id="099d4-262">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-262">Weekend</span></span>    | <span data-ttu-id="099d4-263">za dnia</span><span class="sxs-lookup"><span data-stu-id="099d4-263">daytime</span></span>      | <span data-ttu-id="099d4-264">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-264">inbound</span></span>   | <span data-ttu-id="099d4-265">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-265">x 1.00</span></span>  |
| <span data-ttu-id="099d4-266">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-266">Weekend</span></span>    | <span data-ttu-id="099d4-267">za dnia</span><span class="sxs-lookup"><span data-stu-id="099d4-267">daytime</span></span>      | <span data-ttu-id="099d4-268">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-268">outbound</span></span>  | <span data-ttu-id="099d4-269">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-269">x 1.00</span></span>  |
| <span data-ttu-id="099d4-270">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-270">Weekend</span></span>    | <span data-ttu-id="099d4-271">łazienkowych wieczorem</span><span class="sxs-lookup"><span data-stu-id="099d4-271">evening rush</span></span> | <span data-ttu-id="099d4-272">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-272">inbound</span></span>   | <span data-ttu-id="099d4-273">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-273">x 1.00</span></span>  |
| <span data-ttu-id="099d4-274">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-274">Weekend</span></span>    | <span data-ttu-id="099d4-275">łazienkowych wieczorem</span><span class="sxs-lookup"><span data-stu-id="099d4-275">evening rush</span></span> | <span data-ttu-id="099d4-276">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-276">outbound</span></span>  | <span data-ttu-id="099d4-277">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-277">x 1.00</span></span>  |
| <span data-ttu-id="099d4-278">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-278">Weekend</span></span>    | <span data-ttu-id="099d4-279">procesu na noc</span><span class="sxs-lookup"><span data-stu-id="099d4-279">overnight</span></span>    | <span data-ttu-id="099d4-280">Dla ruchu przychodzącego</span><span class="sxs-lookup"><span data-stu-id="099d4-280">inbound</span></span>   | <span data-ttu-id="099d4-281">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-281">x 1.00</span></span>  |
| <span data-ttu-id="099d4-282">Weekend</span><span class="sxs-lookup"><span data-stu-id="099d4-282">Weekend</span></span>    | <span data-ttu-id="099d4-283">procesu na noc</span><span class="sxs-lookup"><span data-stu-id="099d4-283">overnight</span></span>    | <span data-ttu-id="099d4-284">Wychodzące</span><span class="sxs-lookup"><span data-stu-id="099d4-284">outbound</span></span>  | <span data-ttu-id="099d4-285">x 1.00</span><span class="sxs-lookup"><span data-stu-id="099d4-285">x 1.00</span></span>  |

<span data-ttu-id="099d4-286">Istnieją różne kombinacje 16 trzech zmiennych.</span><span class="sxs-lookup"><span data-stu-id="099d4-286">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="099d4-287">Łącząc niektóre warunki uprościmy wyrażenie switch końcowej.</span><span class="sxs-lookup"><span data-stu-id="099d4-287">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="099d4-288">Korzysta z systemu, który zbiera narzędzia <xref:System.DateTime> struktury przez czas, kiedy płatny był kolekcji.</span><span class="sxs-lookup"><span data-stu-id="099d4-288">The system that collects the tools uses a <xref:System.DateTime> structure for the time when the toll was collection.</span></span> <span data-ttu-id="099d4-289">Tworzenie metody elementu członkowskiego, które Utwórz zmienne z powyższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="099d4-289">Build member methods that create the variables from the preceding table.</span></span>  <span data-ttu-id="099d4-290">Następująca funkcja używa wzorca dopasowania wyrażenie switch programu express czy <xref:System.DateTime> reprezentuje weekend lub dzień tygodnia:</span><span class="sxs-lookup"><span data-stu-id="099d4-290">The following function uses as pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday => true,
        DayOfWeek.Tuesday => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday => true,
        DayOfWeek.Friday => true,
        DayOfWeek.Saturday => false,
        DayOfWeek.Sunday => false
    };
```

<span data-ttu-id="099d4-291">Ta metoda działa, ale jest monotonnych.</span><span class="sxs-lookup"><span data-stu-id="099d4-291">That method works, but it's repetitious.</span></span> <span data-ttu-id="099d4-292">Można uprościć, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="099d4-292">You can simplify it, as shown in the following code:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Saturday,  => false,
        DayOfWeek.Sunday => false,
        _ => true
    };
```

<span data-ttu-id="099d4-293">Możesz wykonać dalszego uproszczenia na to wyrażenie, łącząc dwie wartości w jednym arm:</span><span class="sxs-lookup"><span data-stu-id="099d4-293">You can make a further simplification to this expression by combining the two values into one arm:</span></span>

[!code-csharp[IsWeekDay](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="099d4-294">Następnie dodaj podobną funkcję do kategoryzowania czasu z bloków:</span><span class="sxs-lookup"><span data-stu-id="099d4-294">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="099d4-295">Poprzednia metoda nie używa dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="099d4-295">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="099d4-296">Jest bardziej zrozumiały, przy użyciu dobrze znanych kolejne `if` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="099d4-296">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="099d4-297">Dodaj prywatnej `enum` do przekonwertowania każdego zakresu czasu wartości dyskretnych.</span><span class="sxs-lookup"><span data-stu-id="099d4-297">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="099d4-298">Po utworzeniu tych metod, możesz użyć innej `switch` wyrażenie **wzór krotki** do obliczania cenowej premium.</span><span class="sxs-lookup"><span data-stu-id="099d4-298">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="099d4-299">Można utworzyć `switch` wyrażenia z wszystkich arms 16:</span><span class="sxs-lookup"><span data-stu-id="099d4-299">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="099d4-300">Powyżej kod działa, ale można uprościć.</span><span class="sxs-lookup"><span data-stu-id="099d4-300">The above code works, but it can be simplified.</span></span> <span data-ttu-id="099d4-301">Wszystkie kombinacje osiem for weekend mają ten sam numer płatny.</span><span class="sxs-lookup"><span data-stu-id="099d4-301">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="099d4-302">Możesz zastąpić wszystkie osiem następującym wierszem co:</span><span class="sxs-lookup"><span data-stu-id="099d4-302">You can replace all eight with the following one line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="099d4-303">Ruchu przychodzącego i wychodzącego mają ten sam mnożnik podczas za dzień tygodnia, dnia i godziny na następny dzień.</span><span class="sxs-lookup"><span data-stu-id="099d4-303">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="099d4-304">Arms tych czterech przełącznika, można zastąpić następujące dwa wiersze:</span><span class="sxs-lookup"><span data-stu-id="099d4-304">Those four switch arms can be replaced with the follow two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _) => 1.5m,
```

<span data-ttu-id="099d4-305">Kod powinien wyglądać podobnie do poniższego kodu, po wprowadzeniu tych dwóch zmian:</span><span class="sxs-lookup"><span data-stu-id="099d4-305">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true) => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime, _) => 1.50m,
        (true, TimeBand.EveningRush, true) => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight, _) => 0.75m,
        (false, _, _) => 1.00m,
    };
```

<span data-ttu-id="099d4-306">Na koniec można usunąć łazienkowych dwie godziny prób wina regularne.</span><span class="sxs-lookup"><span data-stu-id="099d4-306">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="099d4-307">Po usunięciu tych arms można zastąpić `false` odrzucić (`_`) w usłudze arm końcowego przełącznika.</span><span class="sxs-lookup"><span data-stu-id="099d4-307">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="099d4-308">Będziesz mieć następującą metodę zakończono:</span><span class="sxs-lookup"><span data-stu-id="099d4-308">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="099d4-309">W tym przykładzie podkreślono jedną z zalet dopasowywania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="099d4-309">This example highlights one of the advantages of pattern matching.</span></span> <span data-ttu-id="099d4-310">Wzorzec gałęzie, które są obliczane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="099d4-310">The pattern branches are evaluated in order.</span></span> <span data-ttu-id="099d4-311">Jeśli można ponownie rozmieścić je tak, aby starszych gałęzi obsługuje jedną ze spraw nowsze kompilatora ostrzega o.</span><span class="sxs-lookup"><span data-stu-id="099d4-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you.</span></span> <span data-ttu-id="099d4-312">Te reguły języka wprowadzone wykonaj poprzedni definiowaniu bez obaw, że kod nie został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="099d4-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="099d4-313">Dopasowanie wzorca zapewnia naturalnych składni wdrożenia różnych rozwiązań, nie należy utworzyć Jeśli używane techniki zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="099d4-313">Pattern matching provides a natural syntax to implement different solutions than you'd create if you used object-oriented techniques.</span></span> <span data-ttu-id="099d4-314">Chmura jest przyczyną, danych i funkcji na żywo od siebie.</span><span class="sxs-lookup"><span data-stu-id="099d4-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="099d4-315">*Kształt* danych i *operacji* na jej nie są zawsze opisane ze sobą.</span><span class="sxs-lookup"><span data-stu-id="099d4-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="099d4-316">W tym samouczku istniejące dane jest używane w całkowicie różnych sposobów z jego funkcja pierwotna.</span><span class="sxs-lookup"><span data-stu-id="099d4-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="099d4-317">Dopasowanie wzorca udostępniła Ci możliwość pisania tego over tych typów, funkcji, mimo że nie można rozszerzyć je.</span><span class="sxs-lookup"><span data-stu-id="099d4-317">Pattern matching gave you the ability to write functionality that over those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="099d4-318">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="099d4-318">Next steps</span></span>

<span data-ttu-id="099d4-319">Możesz pobrać gotowy kod z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="099d4-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="099d4-320">Poznawanie wzorców na własną rękę, a następnie dodaj tej techniki do regularnego działaniach kodowania.</span><span class="sxs-lookup"><span data-stu-id="099d4-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="099d4-321">Tych technik uczenia umożliwia innym sposobem podejście do problemów i Utwórz nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="099d4-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
