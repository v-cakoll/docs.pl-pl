---
title: Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017
description: Dowiedz się, jak tworzyć kompletnego rozwiązania .NET Core w programie Visual Studio 2017 na Windows.
author: bleroy
ms.date: 11/16/2016
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0130ae10cc3bac445892faf0f9a18cf2f23dc036
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170525"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a><span data-ttu-id="7b250-103">Tworzenie kompletnego rozwiązania .NET Core w Windows, przy użyciu programu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b250-103">Building a complete .NET Core solution on Windows, using Visual Studio 2017</span></span>

<span data-ttu-id="7b250-104">Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b250-104">Visual Studio 2017 provides a full-featured development environment for developing .NET Core applications.</span></span> <span data-ttu-id="7b250-105">Procedury przedstawione w tym dokumencie opisano czynności, które są niezbędne do utworzenia typowe rozwiązania .NET Core, który zawiera biblioteki do ponownego wykorzystania, testowania i korzystanie z bibliotek innych firm.</span><span class="sxs-lookup"><span data-stu-id="7b250-105">The procedures in this document describe the steps necessary to build a typical .NET Core solution that includes reusable libraries, testing, and using third-party libraries.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="7b250-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7b250-106">Prerequisites</span></span>

<span data-ttu-id="7b250-107">Postępuj zgodnie z instrukcjami [naszą stronę wymagań wstępnych](../windows-prerequisites.md) na zaktualizowanie środowiska.</span><span class="sxs-lookup"><span data-stu-id="7b250-107">Follow the instructions on [our prerequisites page](../windows-prerequisites.md) to update your environment.</span></span>

## <a name="a-solution-using-only-net-core-projects"></a><span data-ttu-id="7b250-108">Rozwiązanie z użyciem tylko w projektach .NET Core</span><span class="sxs-lookup"><span data-stu-id="7b250-108">A solution using only .NET Core projects</span></span>

### <a name="writing-the-library"></a><span data-ttu-id="7b250-109">Zapisywanie w bibliotece</span><span class="sxs-lookup"><span data-stu-id="7b250-109">Writing the library</span></span>

1. <span data-ttu-id="7b250-110">W programie Visual Studio, wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="7b250-110">In Visual Studio, choose **File**, **New**, **Project**.</span></span> <span data-ttu-id="7b250-111">W **nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła i wybierz polecenie **.NET Standard** węzła, a następnie wybierz **biblioteki klas (.NET Standard)**.</span><span class="sxs-lookup"><span data-stu-id="7b250-111">In the **New Project** dialog, expand the **Visual C#** node and choose the **.NET Standard** node, and then choose **Class Library (.NET Standard)**.</span></span> <span data-ttu-id="7b250-112">Spowoduje to utworzenie biblioteki .NET Standard, który jest przeznaczony dla platformy .NET Core oraz ewentualne innych implementacji .NET, która obsługuje wersję 2.0 [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="7b250-112">This creates a .NET Standard library that targets .NET Core as well as any other .NET implementation that supports version 2.0 of the [.NET Standard](../../standard/net-standard.md).</span></span>

2. <span data-ttu-id="7b250-113">Nazwa projektu "Library" i "Golden" rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7b250-113">Name the project "Library" and the solution "Golden".</span></span> <span data-ttu-id="7b250-114">Pozostaw **Utwórz katalog rozwiązania** zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="7b250-114">Leave **Create directory for solution** checked.</span></span> <span data-ttu-id="7b250-115">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="7b250-115">Click **OK**.</span></span>

3. <span data-ttu-id="7b250-116">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Zarządzaj pakietami NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7b250-116">In Solution Explorer, open the context menu for the **Dependencies** node and choose **Manage NuGet Packages**.</span></span>

4. <span data-ttu-id="7b250-117">Wybierz pozycję "nuget.org" jako **źródła pakietu**i wybierz polecenie **Przeglądaj** kartę. Przeglądaj w poszukiwaniu **Newtonsoft.Json**.</span><span class="sxs-lookup"><span data-stu-id="7b250-117">Choose "nuget.org" as the **Package source**, and choose the **Browse** tab. Browse for **Newtonsoft.Json**.</span></span> <span data-ttu-id="7b250-118">Kliknij przycisk **zainstalować**i zaakceptuj umowę licencyjną.</span><span class="sxs-lookup"><span data-stu-id="7b250-118">Click **Install**, and accept the license agreement.</span></span> <span data-ttu-id="7b250-119">Pakiet powinien zostać wyświetlony w obszarze **zależności/NuGet** i automatycznie przywrócony.</span><span class="sxs-lookup"><span data-stu-id="7b250-119">The package should now appear under **Dependencies/NuGet** and be automatically restored.</span></span>

5. <span data-ttu-id="7b250-120">Zmień nazwę `Class1.cs` plik `Thing.cs`.</span><span class="sxs-lookup"><span data-stu-id="7b250-120">Rename the `Class1.cs` file to `Thing.cs`.</span></span> <span data-ttu-id="7b250-121">Zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="7b250-121">Accept the rename of the class.</span></span> <span data-ttu-id="7b250-122">Dodaj metodę: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span><span class="sxs-lookup"><span data-stu-id="7b250-122">Add a method: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`</span></span>

7. <span data-ttu-id="7b250-123">Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="7b250-123">On the **Build** menu, choose **Build Solution**.</span></span>

   <span data-ttu-id="7b250-124">Rozwiązania należy utworzyć bez błędów.</span><span class="sxs-lookup"><span data-stu-id="7b250-124">The solution should build without error.</span></span>

### <a name="writing-the-test-project"></a><span data-ttu-id="7b250-125">Trwa zapisywanie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="7b250-125">Writing the test project</span></span>

1. <span data-ttu-id="7b250-126">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla **rozwiązania** węzeł i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="7b250-126">In Solution Explorer, open the context menu for the **Solution** node and choose **Add**, **New Project**.</span></span> <span data-ttu-id="7b250-127">W **nowy projekt** okna dialogowego, w obszarze **Visual C# / .NET Core**, wybierz **projekt testów jednostkowych (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="7b250-127">In the **New Project** dialog, under **Visual C# / .NET Core**, choose **Unit Test Project (.NET Core)**.</span></span> <span data-ttu-id="7b250-128">Nadaj mu nazwę "TestLibrary", a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="7b250-128">Name it "TestLibrary" and click OK.</span></span> 

2. <span data-ttu-id="7b250-129">W **TestLibrary** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="7b250-129">In the **TestLibrary** project, open the context menu for the **Dependencies** node and choose **Add Reference**.</span></span> <span data-ttu-id="7b250-130">Kliknij przycisk **projektów**, a następnie zaznacz projekt biblioteki i kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="7b250-130">Click **Projects**, then check the Library project and click OK.</span></span> <span data-ttu-id="7b250-131">Dodaje to odwołanie do biblioteki w projekcie testowym.</span><span class="sxs-lookup"><span data-stu-id="7b250-131">This adds a reference to your library from the test project.</span></span>

3. <span data-ttu-id="7b250-132">Zmień nazwę `UnitTest1.cs` plik `LibraryTests.cs` i zaakceptować zmiany nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="7b250-132">Rename the `UnitTest1.cs` file to `LibraryTests.cs` and accept the class rename.</span></span> <span data-ttu-id="7b250-133">Dodaj `using Library;` na początku pliku i Zastąp `TestMethod1` metoda następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="7b250-133">Add `using Library;` to the top of the file, and replace the `TestMethod1` method with the following code:</span></span>
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   <span data-ttu-id="7b250-134">Powinny teraz być zdolny do skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7b250-134">You should now be able to build the solution.</span></span> 
   
4. <span data-ttu-id="7b250-135">Na **Test** menu, wybierz **Windows**, **Eksploratora testów** Aby uruchomić okno Eksploratora testów do obszaru roboczego.</span><span class="sxs-lookup"><span data-stu-id="7b250-135">On the **Test** menu, choose **Windows**, **Test Explorer** in order to get the test explorer window into your workspace.</span></span> <span data-ttu-id="7b250-136">Po kilku sekundach `ThingGetsObjectValFromNumber` test powinien zostać wyświetlony w Eksploratorze testów.</span><span class="sxs-lookup"><span data-stu-id="7b250-136">After a few seconds, the `ThingGetsObjectValFromNumber` test should appear in the test explorer.</span></span> <span data-ttu-id="7b250-137">Wybierz **uruchomić wszystkie**.</span><span class="sxs-lookup"><span data-stu-id="7b250-137">Choose **Run All**.</span></span>
   
   <span data-ttu-id="7b250-138">Test powinien zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7b250-138">The test should pass.</span></span>

### <a name="writing-the-console-app"></a><span data-ttu-id="7b250-139">Pisanie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="7b250-139">Writing the console app</span></span>

1. <span data-ttu-id="7b250-140">W Eksploratorze rozwiązań Otwórz menu kontekstowe dla rozwiązania, a następnie dodaj nową **Aplikacja konsoli (.NET Core)** projektu.</span><span class="sxs-lookup"><span data-stu-id="7b250-140">In Solution Explorer, open the context menu for the solution, and add a new **Console App (.NET Core)** project.</span></span> <span data-ttu-id="7b250-141">Nadaj mu nazwę "Aplikacja".</span><span class="sxs-lookup"><span data-stu-id="7b250-141">Name it "App".</span></span>

2. <span data-ttu-id="7b250-142">W **aplikacji** projektu, otwórz menu kontekstowe dla **zależności** węzeł i wybierz polecenie **Dodaj**, **odwołania**.</span><span class="sxs-lookup"><span data-stu-id="7b250-142">In the **App** project, open the context menu for the **Dependencies** node and choose **Add**,  **Reference**.</span></span> 

3. <span data-ttu-id="7b250-143">W **Menadżer odwołań** okno dialogowe, sprawdź **biblioteki** w obszarze **projektów**, **rozwiązania** węzłem, a następnie kliknij przycisk **OK**</span><span class="sxs-lookup"><span data-stu-id="7b250-143">In the **Reference Manager** dialog, check **Library** under the **Projects**, **Solution** node, and then click **OK**</span></span>

6. <span data-ttu-id="7b250-144">Otwórz menu kontekstowe dla **aplikacji** węzeł i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="7b250-144">Open the context menu for the **App** node and choose **Set as StartUp Project**.</span></span> <span data-ttu-id="7b250-145">Daje to gwarancję, że naciśnięcie F5 lub CTRL + F5 zostanie uruchomiona aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="7b250-145">This ensures that hitting F5 or CTRL+F5 will start the console app.</span></span>

7. <span data-ttu-id="7b250-146">Otwórz `Program.cs` Dodaj `using Library;` dyrektywę w górnej części pliku, a następnie dodaj `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7b250-146">Open the `Program.cs` file, add a `using Library;` directive to the top of the file, and then add `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` to the `Main` method.</span></span>

8. <span data-ttu-id="7b250-147">Ustaw punkt przerwania po wierszu, który właśnie został dodany.</span><span class="sxs-lookup"><span data-stu-id="7b250-147">Set a breakpoint after the line that you just added.</span></span>

9. <span data-ttu-id="7b250-148">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="7b250-148">Press F5 to run the application.</span></span>

   <span data-ttu-id="7b250-149">Aplikacja powinien być kompilowany bez błędów i powinna trafiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="7b250-149">The application should build without error, and should hit the breakpoint.</span></span> <span data-ttu-id="7b250-150">Należy również możliwość sprawdzenia, czy dane wyjściowe aplikacji, "odpowiedź brzmi 42.".</span><span class="sxs-lookup"><span data-stu-id="7b250-150">You should also be able to check that the application output "The answer is 42.".</span></span>
