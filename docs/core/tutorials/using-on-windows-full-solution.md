---
title: "Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r."
description: "Dowiedz się, jak tworzyć kompletne rozwiązanie .NET Core w Visual Studio 2017 w systemie Windows."
keywords: .NET, .NET core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.openlocfilehash: 694201c1a2a2c373f62b0e0d8e3c1d8aa7e6e881
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="6b0ff-104">Tworzenie kompletnego rozwiązania .NET Core w systemie Windows, przy użyciu programu Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-104">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="6b0ff-105">Visual Studio 2017 udostępnia środowisko deweloperskie kompletne umożliwiający projektowanie aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-105">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="6b0ff-106">Procedury przedstawione w tym dokumencie opisano kroki niezbędne do utworzenia typowe rozwiązania .NET Core, które zawiera biblioteki wielokrotnego użytku, testowania i korzystanie z bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-106">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="6b0ff-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6b0ff-107">Prerequisites</span></span>

<span data-ttu-id="6b0ff-108">Postępuj zgodnie z instrukcjami [naszą stronę wymagania wstępne](../windows-prerequisites.md) aktualizacji środowiska.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-108">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="6b0ff-109">Rozwiązanie przy użyciu tylko projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="6b0ff-109">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="6b0ff-110">Pisanie biblioteki</span><span class="sxs-lookup"><span data-stu-id="6b0ff-110">Writing the library</span></span>

1. <span data-ttu-id="6b0ff-111">W programie Visual Studio, wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-111">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="6b0ff-112">W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzeł, a następnie wybierz pozycję **biblioteki klas (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-112">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="6b0ff-113">Nazwa projektu, "Library" i "Golden" rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="6b0ff-114">Pozostaw **Utwórz katalog rozwiązania** zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="6b0ff-115">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-115">Click **OK**.</span></span>

3. <span data-ttu-id="6b0ff-116">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="6b0ff-117">Wybierz polecenie "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="6b0ff-118">Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="6b0ff-119">Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie go przywrócić.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="6b0ff-120">Zmień nazwę `Class1.cs` pliku `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="6b0ff-121">Zaakceptuj zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-121">Accept the rename of the class.</span></span> <span data-ttu-id="6b0ff-122">Dodaj metodę:`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="6b0ff-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="6b0ff-123">Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="6b0ff-124">Rozwiązanie powinno utworzyć bez błędów.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="6b0ff-125">Zapisywanie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="6b0ff-125">Writing the test project</span></span>

1. <span data-ttu-id="6b0ff-126">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="6b0ff-127">W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **jednostkowy projekt testowy (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="6b0ff-128">Nadaj jej nazwę na "TestLibrary", a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="6b0ff-129">W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="6b0ff-130">Kliknij przycisk **projektów**, sprawdź projektu biblioteki i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="6b0ff-131">Spowoduje to dodanie odwołania do biblioteki z projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="6b0ff-132">Zmień nazwę `UnitTest1.cs` pliku `LibraryTests.cs` i zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="6b0ff-133">Dodaj `using Library;` na początku pliku i Zamień `TestMethod1` metodę z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="6b0ff-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="6b0ff-134">Teraz można skompilować.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="6b0ff-135">Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="6b0ff-136">Po kilku sekundach `ThingGetsObjectValFromNumber` testu powinien zostać wyświetlony w Eksploratorze testów.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="6b0ff-137">Wybierz **uruchomić wszystkie**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="6b0ff-138">Należy przekazać testu.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="6b0ff-139">Pisanie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="6b0ff-139">Writing the console app</span></span>

1. <span data-ttu-id="6b0ff-140">W Eksploratorze rozwiązań Otwórz menu kontekstowego dla rozwiązania, a następnie dodaj nową **aplikacji konsoli (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="6b0ff-141">Nazwę "Aplikacja".</span><span class="sxs-lookup"><span data-stu-id="6b0ff-141">Name it "App".</span></span>

2. <span data-ttu-id="6b0ff-142">W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="6b0ff-143">W **Menedżera odwołań** dialogowym wyboru **biblioteki** w obszarze **projekty**, **rozwiązania** węzeł, a następnie kliknij przycisk **OK**</span><span class="sxs-lookup"><span data-stu-id="6b0ff-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="6b0ff-144">Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="6b0ff-145">Dzięki temu, że naciśnięcie klawisza F5 lub CTRL + F5 rozpocznie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="6b0ff-146">Otwórz `Program.cs` plików, dodawanie `using Library;` dyrektywy na początku pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` — metoda.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="6b0ff-147">Ustaw punkt przerwania po wierszu, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="6b0ff-148">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-148">Press F5 to run the application..</span></span>

   <span data-ttu-id="6b0ff-149">Aplikacja powinno utworzyć bez błędów, a powinien trafienie punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="6b0ff-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="6b0ff-150">Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji "odpowiedź jest 42.".</span><span class="sxs-lookup"><span data-stu-id="6b0ff-150">You should also be able to check that the application output "The answer is 42.".</span></span>
