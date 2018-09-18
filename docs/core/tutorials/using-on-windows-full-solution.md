---
title: Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017
description: Dowiedz się, jak tworzyć kompletnego rozwiązania .NET Core w programie Visual Studio 2017 na Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: 15537ea8c68b5c873bbf26ab0519a19de0b13230
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45969564"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="c87e0-103">Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c87e0-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="c87e0-104">Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c87e0-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="c87e0-105">Procedury przedstawione w tym dokumencie opisano czynności, które są niezbędne do utworzenia typowe rozwiązania .NET Core, który zawiera biblioteki do ponownego wykorzystania, testowania i korzystanie z bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="c87e0-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="c87e0-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c87e0-106">Prerequisites</span></span>

<span data-ttu-id="c87e0-107">Postępuj zgodnie z instrukcjami [naszą stronę wymagań wstępnych](../windows-prerequisites.md) na zaktualizowanie środowiska.</span><span class="sxs-lookup"><span data-stu-id="c87e0-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="c87e0-108">Rozwiązanie z użyciem tylko w projektach .NET Core</span><span class="sxs-lookup"><span data-stu-id="c87e0-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="c87e0-109">Zapisywanie w bibliotece</span><span class="sxs-lookup"><span data-stu-id="c87e0-109">Writing the library</span></span>

1. <span data-ttu-id="c87e0-110">W programie Visual Studio, wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="c87e0-111">W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzła, a następnie wybierz **biblioteki klas (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> 

2. <span data-ttu-id="c87e0-112">Nazwa projektu "Library" i "Golden" rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c87e0-112">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="c87e0-113">Pozostaw **Utwórz katalog rozwiązania** zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="c87e0-113">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="c87e0-114">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-114">Click **OK**.</span></span>

3. <span data-ttu-id="c87e0-115">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-115">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="c87e0-116">Wybierz pozycję "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-116">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="c87e0-117">Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="c87e0-117">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="c87e0-118">Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie przywrócony.</span><span class="sxs-lookup"><span data-stu-id="c87e0-118">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="c87e0-119">Zmień nazwę `Class1.cs` plik `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="c87e0-119">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="c87e0-120">Zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="c87e0-120">Accept the rename of the class.</span></span> <span data-ttu-id="c87e0-121">Dodaj metodę: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="c87e0-121">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="c87e0-122">Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-122">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="c87e0-123">Rozwiązania należy utworzyć bez błędów.</span><span class="sxs-lookup"><span data-stu-id="c87e0-123">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="c87e0-124">Trwa zapisywanie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="c87e0-124">Writing the test project</span></span>

1. <span data-ttu-id="c87e0-125">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-125">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="c87e0-126">W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **projekt testów jednostkowych (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-126">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="c87e0-127">Nadaj mu nazwę "TestLibrary", a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="c87e0-127">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="c87e0-128">W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-128">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="c87e0-129">Kliknij przycisk **projektów**, a następnie zaznacz projekt biblioteki i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="c87e0-129">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="c87e0-130">Dodaje to odwołanie do biblioteki w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="c87e0-130">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="c87e0-131">Zmień nazwę `UnitTest1.cs` plik `LibraryTests.cs` i zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="c87e0-131">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="c87e0-132">Dodaj `using Library;` na początku pliku i Zastąp `TestMethod1` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="c87e0-132">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="c87e0-133">Powinny teraz być zdolny do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c87e0-133">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="c87e0-134">Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="c87e0-134">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="c87e0-135">Po kilku sekundach `ThingGetsObjectValFromNumber` test powinien zostać wyświetlony w Eksploratorze testów.</span><span class="sxs-lookup"><span data-stu-id="c87e0-135">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="c87e0-136">Wybierz **uruchomić wszystkie**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-136">Choose **Run All**.</span></span>
   
   <span data-ttu-id="c87e0-137">Test powinien zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c87e0-137">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="c87e0-138">Pisanie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="c87e0-138">Writing the console app</span></span>

1. <span data-ttu-id="c87e0-139">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla rozwiązania, a następnie dodaj nową **Aplikacja konsoli (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="c87e0-139">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="c87e0-140">Nadaj mu nazwę "Aplikacja".</span><span class="sxs-lookup"><span data-stu-id="c87e0-140">Name it "App".</span></span>

2. <span data-ttu-id="c87e0-141">W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-141">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="c87e0-142">W **Menadżer odwołań** okno dialogowe, sprawdź **biblioteki** w obszarze **projektów**, **rozwiązania** węzłem, a następnie kliknij przycisk **OK**</span><span class="sxs-lookup"><span data-stu-id="c87e0-142">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="c87e0-143">Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="c87e0-143">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="c87e0-144">Daje to gwarancję, że naciśnięcie F5 lub CTRL + F5 zostanie uruchomiona aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="c87e0-144">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="c87e0-145">Otwórz `Program.cs` Dodaj `using Library;` dyrektywę w górnej części pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c87e0-145">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="c87e0-146">Ustaw punkt przerwania po wierszu, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="c87e0-146">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="c87e0-147">Naciśnij klawisz F5, aby uruchomić aplikację...</span><span class="sxs-lookup"><span data-stu-id="c87e0-147">Press F5 to run the application..</span></span>

   <span data-ttu-id="c87e0-148">Aplikacja powinien być kompilowany bez błędów i powinna trafiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="c87e0-148">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="c87e0-149">Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji, "odpowiedź brzmi 42.".</span><span class="sxs-lookup"><span data-stu-id="c87e0-149">You should also be able to check that the application output "The answer is 42.".</span></span>
