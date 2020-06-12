---
title: Testowanie biblioteki klas .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio Code
description: Utwórz projekt testu jednostkowego dla biblioteki klas .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
ms.date: 06/08/2020
ms.openlocfilehash: a61fd952eea2dec0d5a9f351d3f3d01c738e8fad
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701036"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio-code"></a><span data-ttu-id="c082d-104">Samouczek: testowanie biblioteki klas .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c082d-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="c082d-105">W tym samouczku pokazano, jak zautomatyzować testy jednostkowe przez dodanie projektu testowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c082d-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c082d-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c082d-106">Prerequisites</span></span>

- <span data-ttu-id="c082d-107">Ten samouczek współdziała z rozwiązaniem tworzonym w temacie [Tworzenie biblioteki .NET standard w Visual Studio Code](library-with-visual-studio-code.md).</span><span class="sxs-lookup"><span data-stu-id="c082d-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="c082d-108">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="c082d-108">Create a unit test project</span></span>

<span data-ttu-id="c082d-109">Testy jednostkowe zapewniają zautomatyzowane testowanie oprogramowania podczas opracowywania i publikowania.</span><span class="sxs-lookup"><span data-stu-id="c082d-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="c082d-110">Platforma testowa używana w tym samouczku to MSTest.</span><span class="sxs-lookup"><span data-stu-id="c082d-110">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="c082d-111">[MSTest](https://github.com/Microsoft/testfx-docs) jest jednym z trzech platform testowych, spośród których można dokonać wyboru.</span><span class="sxs-lookup"><span data-stu-id="c082d-111">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="c082d-112">Inne to [xUnit](https://xunit.net/) i [nunit](https://nunit.org/).</span><span class="sxs-lookup"><span data-stu-id="c082d-112">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="c082d-113">Uruchom program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c082d-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="c082d-114">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w temacie [tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c082d-114">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="c082d-115">Utwórz projekt testu jednostkowego o nazwie "StringLibraryTest".</span><span class="sxs-lookup"><span data-stu-id="c082d-115">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="c082d-116">Szablon projektu tworzy plik UnitTest1.cs o następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c082d-116">The project template creates a UnitTest1.cs file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="c082d-117">Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c082d-117">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="c082d-118">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="c082d-118">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="c082d-119">Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut do `UnitTest1` klasy.</span><span class="sxs-lookup"><span data-stu-id="c082d-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="c082d-120">Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do zdefiniowania `TestMethod1` .</span><span class="sxs-lookup"><span data-stu-id="c082d-120">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="c082d-121">Każda metoda oznaczona przy użyciu elementu [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) w klasie testowej oznaczona przy użyciu elementu [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) jest wykonywana automatycznie, gdy test jednostkowy jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="c082d-121">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="c082d-122">Dodaj projekt testowy do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c082d-122">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="c082d-123">Dodaj odwołanie do projektu</span><span class="sxs-lookup"><span data-stu-id="c082d-123">Add a project reference</span></span>

<span data-ttu-id="c082d-124">Aby projekt testowy mógł współpracował z `StringLibrary` klasą, Dodaj odwołanie w `StringLibraryTest` projekcie do `StringLibrary` projektu.</span><span class="sxs-lookup"><span data-stu-id="c082d-124">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="c082d-125">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="c082d-125">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="c082d-126">Dodawanie i uruchamianie metod testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="c082d-126">Add and run unit test methods</span></span>

<span data-ttu-id="c082d-127">Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutem w klasie, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="c082d-127">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="c082d-128">Metoda testowa kończy się po znalezieniu pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c082d-128">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="c082d-129">Najczęstsze testy wywołują elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasy.</span><span class="sxs-lookup"><span data-stu-id="c082d-129">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="c082d-130">Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu.</span><span class="sxs-lookup"><span data-stu-id="c082d-130">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="c082d-131">`Assert`W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod:</span><span class="sxs-lookup"><span data-stu-id="c082d-131">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="c082d-132">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="c082d-132">Assert methods</span></span>     | <span data-ttu-id="c082d-133">Funkcja</span><span class="sxs-lookup"><span data-stu-id="c082d-133">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="c082d-134">Sprawdza, czy dwie wartości lub obiekty są równe.</span><span class="sxs-lookup"><span data-stu-id="c082d-134">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="c082d-135">Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe.</span><span class="sxs-lookup"><span data-stu-id="c082d-135">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="c082d-136">Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="c082d-136">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="c082d-137">Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="c082d-137">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="c082d-138">Sprawdza, czy warunek to `false` .</span><span class="sxs-lookup"><span data-stu-id="c082d-138">Verifies that a condition is `false`.</span></span> <span data-ttu-id="c082d-139">Potwierdzenie kończy się niepowodzeniem, jeśli warunek ma wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="c082d-139">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="c082d-140">Sprawdza, czy obiekt nie jest `null` .</span><span class="sxs-lookup"><span data-stu-id="c082d-140">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="c082d-141">Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null` .</span><span class="sxs-lookup"><span data-stu-id="c082d-141">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="c082d-142">Można również użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metody w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="c082d-142">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="c082d-143">Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="c082d-143">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="c082d-144">W testowaniu `StringLibrary.StartsWithUpper` metody, należy podać kilka ciągów zaczynających się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="c082d-144">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="c082d-145">Oczekiwano, że metoda zwraca `true` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="c082d-145">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c082d-146">Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="c082d-146">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="c082d-147">Oczekiwano, że metoda zwraca `false` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="c082d-147">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c082d-148">Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg ( `String.Empty` )](xref:System.String.Empty) i a i `null` ciąg.</span><span class="sxs-lookup"><span data-stu-id="c082d-148">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="c082d-149">Pusty ciąg jest taki, który nie zawiera znaków i <xref:System.String.Length> ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="c082d-149">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="c082d-150">`null`Ciąg to taki, który nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="c082d-150">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="c082d-151">Można wywołać `StartsWithUpper` bezpośrednio jako metodę statyczną i przekazać pojedynczy <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="c082d-151">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="c082d-152">Lub można wywołać `StartsWithUpper` jako metodę rozszerzającą dla `string` zmiennej przypisanej do `null` .</span><span class="sxs-lookup"><span data-stu-id="c082d-152">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="c082d-153">Zdefiniujesz trzy metody, z których każda wywołuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę dla każdego elementu w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="c082d-153">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="c082d-154">Wywołasz Przeciążenie metody, które pozwala określić komunikat o błędzie, który ma być wyświetlany w przypadku niepowodzenia testu.</span><span class="sxs-lookup"><span data-stu-id="c082d-154">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="c082d-155">Komunikat identyfikuje ciąg, który spowodował awarię.</span><span class="sxs-lookup"><span data-stu-id="c082d-155">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="c082d-156">Aby utworzyć metody testowe:</span><span class="sxs-lookup"><span data-stu-id="c082d-156">To create the test methods:</span></span>

1. <span data-ttu-id="c082d-157">Otwórz *StringLibraryTest/UnitTest1. cs* i Zastąp cały kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="c082d-157">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="c082d-158">Test wielkich liter w `TestStartsWithUpper` metodzie zawiera alfabet grecki (u + 0391) oraz wielką literę pauzy (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="c082d-158">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="c082d-159">Test małymi literami w `TestDoesNotStartWithUpper` metodzie obejmuje małą literę alfa (u + 03B1) i małą literę cyrylicy GHE (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="c082d-159">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="c082d-160">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="c082d-160">Save your changes.</span></span>

1. <span data-ttu-id="c082d-161">Uruchom testy:</span><span class="sxs-lookup"><span data-stu-id="c082d-161">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="c082d-162">Dane wyjściowe terminalu pokazują, że wszystkie testy zostały zakończone.</span><span class="sxs-lookup"><span data-stu-id="c082d-162">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="c082d-163">Obsługa niepowodzeń testów</span><span class="sxs-lookup"><span data-stu-id="c082d-163">Handle test failures</span></span>

<span data-ttu-id="c082d-164">Jeśli wykonujesz programowanie sterowane testami (TDD), najpierw napiszesz testy i nie powiodą się po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="c082d-164">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="c082d-165">Następnie dodasz kod do aplikacji, która pomyślnie testuje.</span><span class="sxs-lookup"><span data-stu-id="c082d-165">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="c082d-166">Na potrzeby tego samouczka utworzono test po zapisaniu kodu aplikacji, który jest weryfikowany, więc niepowodzenie testu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c082d-166">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="c082d-167">Aby sprawdzić, czy test zakończy się niepowodzeniem, gdy spodziewasz się niepowodzeniem, Dodaj nieprawidłową wartość do danych wejściowych testu.</span><span class="sxs-lookup"><span data-stu-id="c082d-167">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="c082d-168">Zmodyfikuj `words` tablicę w `TestDoesNotStartWithUpper` metodzie, aby uwzględnić ciąg "Error".</span><span class="sxs-lookup"><span data-stu-id="c082d-168">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="c082d-169">Uruchom testy:</span><span class="sxs-lookup"><span data-stu-id="c082d-169">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="c082d-170">Dane wyjściowe terminalu pokazują, że jeden test zakończy się niepowodzeniem i zawiera komunikat o błędzie dla testu zakończonego niepowodzeniem: "Assert. IsFalse nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c082d-170">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="c082d-171">Oczekiwano dla elementu "Error": false; rzeczywista: true ".</span><span class="sxs-lookup"><span data-stu-id="c082d-171">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="c082d-172">Z powodu błędu nie przetestowano ciągów w tablicy po "błędzie".</span><span class="sxs-lookup"><span data-stu-id="c082d-172">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="c082d-173">Usuń ciąg "Error", który został dodany w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="c082d-173">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="c082d-174">Uruchom ponownie test i testy zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c082d-174">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="c082d-175">Testowanie wersji wydania biblioteki</span><span class="sxs-lookup"><span data-stu-id="c082d-175">Test the Release version of the library</span></span>

<span data-ttu-id="c082d-176">Teraz, gdy testy zostały zakończone przed uruchomieniem kompilacji biblioteki, należy uruchomić testy w dodatkowym czasie względem kompilacji wydania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c082d-176">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="c082d-177">Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.</span><span class="sxs-lookup"><span data-stu-id="c082d-177">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="c082d-178">Uruchom testy z konfiguracją kompilacji wydania:</span><span class="sxs-lookup"><span data-stu-id="c082d-178">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="c082d-179">Testy zostały zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c082d-179">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c082d-180">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="c082d-180">Additional resources</span></span>

* [<span data-ttu-id="c082d-181">Testy jednostkowe w .NET Core i .NET Standard</span><span class="sxs-lookup"><span data-stu-id="c082d-181">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="c082d-182">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c082d-182">Next steps</span></span>

<span data-ttu-id="c082d-183">W tym samouczku przetestowano bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="c082d-183">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="c082d-184">Bibliotekę można udostępniać innym osobom, publikując ją w pakiecie [NuGet](https://nuget.org) jako pakiet.</span><span class="sxs-lookup"><span data-stu-id="c082d-184">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="c082d-185">Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:</span><span class="sxs-lookup"><span data-stu-id="c082d-185">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c082d-186">Tworzenie i publikowanie pakietu przy użyciu interfejsu wiersza polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="c082d-186">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="c082d-187">W przypadku opublikowania biblioteki jako pakietu NuGet inne osoby mogą ją zainstalować i używać.</span><span class="sxs-lookup"><span data-stu-id="c082d-187">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="c082d-188">Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:</span><span class="sxs-lookup"><span data-stu-id="c082d-188">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c082d-189">Instalowanie i używanie pakietu przy użyciu interfejsu wiersza polecenia dotnet</span><span class="sxs-lookup"><span data-stu-id="c082d-189">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="c082d-190">Biblioteka nie musi być dystrybuowana jako pakiet.</span><span class="sxs-lookup"><span data-stu-id="c082d-190">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="c082d-191">Można go powiązać z aplikacją konsolową, która go używa.</span><span class="sxs-lookup"><span data-stu-id="c082d-191">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="c082d-192">Aby dowiedzieć się, jak opublikować aplikację konsolową, zobacz wcześniejszy samouczek w tej serii:</span><span class="sxs-lookup"><span data-stu-id="c082d-192">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c082d-193">Publikowanie aplikacji konsolowej .NET Core za pomocą Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c082d-193">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
