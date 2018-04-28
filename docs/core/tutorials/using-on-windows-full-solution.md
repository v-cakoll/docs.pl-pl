---
title: Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r.
description: Dowiedz się, jak tworzyć kompletne rozwiązanie .NET Core w Visual Studio 2017 w systemie Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8e37eb578f9c4ac63fbc120e6227098ea69d169d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="33cb6-103">Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="33cb6-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="33cb6-104">Visual Studio 2017 udostępnia środowisko deweloperskie kompletne umożliwiający projektowanie aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="33cb6-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="33cb6-105">Procedury przedstawione w tym dokumencie opisano kroki niezbędne do utworzenia typowe rozwiązania .NET Core, które zawiera biblioteki wielokrotnego użytku, testowania i korzystanie z bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="33cb6-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="33cb6-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="33cb6-106">Prerequisites</span></span>

<span data-ttu-id="33cb6-107">Postępuj zgodnie z instrukcjami [naszą stronę wymagania wstępne](../windows-prerequisites.md) aktualizacji środowiska.</span><span class="sxs-lookup"><span data-stu-id="33cb6-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="33cb6-108">Rozwiązanie przy użyciu tylko projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="33cb6-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="33cb6-109">Pisanie biblioteki</span><span class="sxs-lookup"><span data-stu-id="33cb6-109">Writing the library</span></span>

1. <span data-ttu-id="33cb6-110">W programie Visual Studio, wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="33cb6-111">W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzeł, a następnie wybierz pozycję **biblioteki klas (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="33cb6-112">Nazwa projektu, "Library" i "Golden" rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="33cb6-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="33cb6-113">Pozostaw **Utwórz katalog rozwiązania** zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="33cb6-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="33cb6-114">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-114">Click **OK**.</span></span>

3. <span data-ttu-id="33cb6-115">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="33cb6-116">Wybierz polecenie "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="33cb6-117">Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="33cb6-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="33cb6-118">Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie go przywrócić.</span><span class="sxs-lookup"><span data-stu-id="33cb6-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="33cb6-119">Zmień nazwę `Class1.cs` pliku `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="33cb6-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="33cb6-120">Zaakceptuj zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="33cb6-120">Accept the rename of the class.</span></span> <span data-ttu-id="33cb6-121">Dodaj metodę: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="33cb6-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="33cb6-122">Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="33cb6-123">Rozwiązanie powinno utworzyć bez błędów.</span><span class="sxs-lookup"><span data-stu-id="33cb6-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="33cb6-124">Zapisywanie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="33cb6-124">Writing the test project</span></span>

1. <span data-ttu-id="33cb6-125">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="33cb6-126">W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **jednostkowy projekt testowy (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="33cb6-127">Nadaj jej nazwę na "TestLibrary", a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="33cb6-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="33cb6-128">W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="33cb6-129">Kliknij przycisk **projektów**, sprawdź projektu biblioteki i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="33cb6-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="33cb6-130">Spowoduje to dodanie odwołania do biblioteki z projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="33cb6-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="33cb6-131">Zmień nazwę `UnitTest1.cs` pliku `LibraryTests.cs` i zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="33cb6-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="33cb6-132">Dodaj `using Library;` na początku pliku i Zamień `TestMethod1` metodę z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="33cb6-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="33cb6-133">Teraz można skompilować.</span><span class="sxs-lookup"><span data-stu-id="33cb6-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="33cb6-134">Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="33cb6-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="33cb6-135">Po kilku sekundach `ThingGetsObjectValFromNumber` testu powinien zostać wyświetlony w Eksploratorze testów.</span><span class="sxs-lookup"><span data-stu-id="33cb6-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="33cb6-136">Wybierz **uruchomić wszystkie**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="33cb6-137">Należy przekazać testu.</span><span class="sxs-lookup"><span data-stu-id="33cb6-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="33cb6-138">Pisanie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="33cb6-138">Writing the console app</span></span>

1. <span data-ttu-id="33cb6-139">W Eksploratorze rozwiązań Otwórz menu kontekstowego dla rozwiązania, a następnie dodaj nową **aplikacji konsoli (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="33cb6-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="33cb6-140">Nazwę "Aplikacja".</span><span class="sxs-lookup"><span data-stu-id="33cb6-140">Name it "App".</span></span>

2. <span data-ttu-id="33cb6-141">W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="33cb6-142">W **Menedżera odwołań** dialogowym wyboru **biblioteki** w obszarze **projekty**, **rozwiązania** węzeł, a następnie kliknij przycisk **OK**</span><span class="sxs-lookup"><span data-stu-id="33cb6-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="33cb6-143">Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="33cb6-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="33cb6-144">Dzięki temu, że naciśnięcie klawisza F5 lub CTRL + F5 rozpocznie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="33cb6-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="33cb6-145">Otwórz `Program.cs` plików, dodawanie `using Library;` dyrektywy na początku pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` — metoda.</span><span class="sxs-lookup"><span data-stu-id="33cb6-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="33cb6-146">Ustaw punkt przerwania po wierszu, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="33cb6-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="33cb6-147">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="33cb6-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="33cb6-148">Aplikacja powinno utworzyć bez błędów, a powinien trafienie punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="33cb6-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="33cb6-149">Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji "odpowiedź jest 42.".</span><span class="sxs-lookup"><span data-stu-id="33cb6-149">You should also be able to check that the application output "The answer is 42.".</span></span>
