---
title: Testowanie biblioteki klas .NET Standard przy użyciu platformy .NET Core w programie Visual Studio
description: Utwórz projekt testu jednostkowego dla biblioteki klas platformy .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 48ada77b8422030fd93aa29df1df50a3ae5104fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283510"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="ca7f0-104">Samouczek: testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca7f0-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="ca7f0-105">W tym samouczku pokazano, jak zautomatyzować testy jednostkowe przez dodanie projektu testowego do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ca7f0-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ca7f0-106">Prerequisites</span></span>

- <span data-ttu-id="ca7f0-107">Ten samouczek współpracuje z rozwiązaniem tworzonym w temacie [Tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ca7f0-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="ca7f0-108">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="ca7f0-108">Create a unit test project</span></span>

1. <span data-ttu-id="ca7f0-109">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w temacie [tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="ca7f0-109">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="ca7f0-110">Dodaj nowy projekt testu jednostkowego o nazwie "StringLibraryTest" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-110">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="ca7f0-111">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-111">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="ca7f0-112">Na stronie **Dodawanie nowego projektu** wprowadź **MSTest** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-112">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="ca7f0-113">Wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-113">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="ca7f0-114">Wybierz szablon **projekt testu MSTest (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-114">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="ca7f0-115">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibraryTest** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-115">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="ca7f0-116">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-116">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="ca7f0-117">MSTest jest jednym z trzech platform testowych, spośród których można dokonać wyboru.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-117">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="ca7f0-118">Inne to xUnit i nUnit.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-118">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="ca7f0-119">Program Visual Studio tworzy projekt i otwiera plik klasy w oknie kodu przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-119">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="ca7f0-120">Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-120">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="ca7f0-121">Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-121">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="ca7f0-122">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-122">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="ca7f0-123">Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut do `UnitTest1` klasy.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-123">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="ca7f0-124">Stosuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybut do definiowania `TestMethod1` w języku C# lub `TestSub` w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="ca7f0-125">Każda metoda oznaczona przy użyciu elementu [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) w klasie testowej oznaczona przy użyciu elementu [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) jest wykonywana automatycznie, gdy test jednostkowy jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-125">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="ca7f0-126">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie do projektu** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-126">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="ca7f0-127">W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** , a następnie zaznacz pole wyboru obok pozycji **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-127">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="ca7f0-128">Dodanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znalezienie metod **StringLibrary** podczas kompilowania projektu **StringLibraryTest** .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="ca7f0-129">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-129">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="ca7f0-130">Dodawanie i uruchamianie metod testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="ca7f0-130">Add and run unit test methods</span></span>

<span data-ttu-id="ca7f0-131">Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutem w klasie, która jest oznaczona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-131">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="ca7f0-132">Metoda testowa kończy się po znalezieniu pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-132">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="ca7f0-133">Najczęstsze testy wywołują elementy członkowskie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasy.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-133">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="ca7f0-134">Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-134">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="ca7f0-135">`Assert`W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-135">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="ca7f0-136">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="ca7f0-136">Assert methods</span></span>     | <span data-ttu-id="ca7f0-137">Funkcja</span><span class="sxs-lookup"><span data-stu-id="ca7f0-137">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="ca7f0-138">Sprawdza, czy dwie wartości lub obiekty są równe.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-138">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="ca7f0-139">Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-139">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="ca7f0-140">Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-140">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="ca7f0-141">Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-141">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="ca7f0-142">Sprawdza, czy warunek to `false` .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-142">Verifies that a condition is `false`.</span></span> <span data-ttu-id="ca7f0-143">Potwierdzenie kończy się niepowodzeniem, jeśli warunek ma wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-143">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="ca7f0-144">Sprawdza, czy obiekt nie jest `null` .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-144">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="ca7f0-145">Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null` .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-145">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="ca7f0-146">Można również użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> metody w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-146">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="ca7f0-147">Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-147">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="ca7f0-148">W testowaniu `StringLibrary.StartsWithUpper` metody, należy podać kilka ciągów zaczynających się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-148">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="ca7f0-149">Oczekiwano, że metoda zwraca `true` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-149">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ca7f0-150">Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-150">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="ca7f0-151">Oczekiwano, że metoda zwraca `false` w tych przypadkach, więc można wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-151">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ca7f0-152">Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg ( `String.Empty` )](xref:System.String.Empty), prawidłowy ciąg, który nie zawiera znaków i <xref:System.String.Length> ma wartość 0, i `null` ciąg, który nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-152">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="ca7f0-153">Jeśli `StartsWithUpper` jest wywoływana jako metoda rozszerzająca <xref:System.String> wystąpienia, nie można przesłać `null` ciągu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-153">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="ca7f0-154">Można jednak wywołać go bezpośrednio jako metodę statyczną i przekazać pojedynczy <xref:System.String> argument.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-154">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="ca7f0-155">Zdefiniujesz trzy metody, z których każda wywołuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę wielokrotnie dla każdego elementu w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-155">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="ca7f0-156">Ponieważ metoda testowa nie powiedzie się po znalezieniu pierwszego błędu, wywoła Przeciążenie metody, które umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-156">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="ca7f0-157">Aby utworzyć metody testowe:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-157">To create the test methods:</span></span>

1. <span data-ttu-id="ca7f0-158">W oknie kod *UnitTest1.cs* lub *UnitTest1. vb* Zastąp kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-158">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="ca7f0-159">Test wielkich liter w `TestStartsWithUpper` metodzie zawiera alfabet grecki (u + 0391) oraz wielką literę pauzy (u + 041C).</span><span class="sxs-lookup"><span data-stu-id="ca7f0-159">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="ca7f0-160">Test małymi literami w `TestDoesNotStartWithUpper` metodzie obejmuje małą literę alfa (u + 03B1) i małą literę cyrylicy GHE (u + 0433).</span><span class="sxs-lookup"><span data-stu-id="ca7f0-160">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="ca7f0-161">Na pasku menu wybierz pozycję **plik**  >  **Zapisz UnitTest1.cs jako** lub Zapisz **plik**  >  **UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-161">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="ca7f0-162">W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-162">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-163">![Okno dialogowe zapisywania pliku w programie Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-163">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="ca7f0-164">W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **tak** , aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-164">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="ca7f0-165">W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem)-strona kodowa 65001** z listy rozwijanej **kodowanie** i wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-165">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-166">![Zaawansowane opcje zapisywania programu Visual Studio — okno dialogowe](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-166">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="ca7f0-167">Jeśli kod źródłowy nie zostanie zapisany jako plik zakodowany w formacie UTF8, program Visual Studio może go zapisać jako plik ASCII.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-167">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="ca7f0-168">Gdy tak się stanie, środowisko uruchomieniowe nie dekoduje znaków UTF8 poza zakresem ASCII, a wyniki testu nie będą poprawne.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-168">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="ca7f0-169">Na pasku menu wybierz kolejno opcje **test**  >  **Uruchom wszystkie testy**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-169">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="ca7f0-170">Jeśli okno **Eksplorator testów** nie jest otwarte, otwórz je, wybierając **Testuj**  >  **Eksploratora testów**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-170">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="ca7f0-171">Trzy testy są wymienione w sekcji **testy zakończone** , a sekcja **podsumowania** raportuje wynik przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-171">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-172">![Okno Eksploratora testów z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-172">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="ca7f0-173">Obsługa niepowodzeń testów</span><span class="sxs-lookup"><span data-stu-id="ca7f0-173">Handle test failures</span></span>

<span data-ttu-id="ca7f0-174">Jeśli wykonujesz programowanie sterowane testami (TDD), najpierw napiszesz testy i nie powiodą się po raz pierwszy.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-174">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="ca7f0-175">Następnie dodasz kod do aplikacji, która pomyślnie testuje.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-175">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="ca7f0-176">W takim przypadku został utworzony test po zapisaniu kodu aplikacji, który jest weryfikowany, więc niepowodzenie testu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-176">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="ca7f0-177">Aby sprawdzić, czy test zakończy się niepowodzeniem, gdy spodziewasz się niepowodzeniem, Dodaj nieprawidłową wartość do danych wejściowych testu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-177">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="ca7f0-178">Zmodyfikuj `words` tablicę w `TestDoesNotStartWithUpper` metodzie, aby uwzględnić ciąg "Error".</span><span class="sxs-lookup"><span data-stu-id="ca7f0-178">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="ca7f0-179">Nie musisz zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki w przypadku skompilowania rozwiązania do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-179">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="ca7f0-180">Uruchom test, wybierając pozycję **test**  >  **Uruchom wszystkie testy** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-180">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="ca7f0-181">Okno **Eksplorator testów** wskazuje, że dwa testy zostały wykonane pomyślnie i jeden z nich zakończył się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-181">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-182">![Okno Eksploratora testów z niepowodzeniem testami](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-182">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="ca7f0-183">Wybierz test zakończony niepowodzeniem `TestDoesNotStartWith` .</span><span class="sxs-lookup"><span data-stu-id="ca7f0-183">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="ca7f0-184">W oknie **Eksplorator testów** zostanie wyświetlony komunikat utworzony przez potwierdzenie: "Assert. IsFalse nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-184">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="ca7f0-185">Oczekiwano dla elementu "Error": false; rzeczywista: true ".</span><span class="sxs-lookup"><span data-stu-id="ca7f0-185">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="ca7f0-186">Z powodu błędu nie przetestowano wszystkich ciągów w tablicy po "błędzie".</span><span class="sxs-lookup"><span data-stu-id="ca7f0-186">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-187">![Okno Eksploratora testów przedstawiające błąd potwierdzenia IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-187">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="ca7f0-188">Cofnij modyfikację w kroku 1 i usuń ciąg "Error".</span><span class="sxs-lookup"><span data-stu-id="ca7f0-188">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="ca7f0-189">Uruchom ponownie test i testy zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-189">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="ca7f0-190">Testowanie wersji wydania biblioteki</span><span class="sxs-lookup"><span data-stu-id="ca7f0-190">Test the Release version of the library</span></span>

<span data-ttu-id="ca7f0-191">Teraz, gdy testy zostały zakończone, gdy uruchamiasz wersję debugową biblioteki, Uruchom testy w dodatkowym czasie względem kompilacji wydania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-191">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="ca7f0-192">Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="ca7f0-193">Aby przetestować kompilację wydania:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-193">To test the Release build:</span></span>

1. <span data-ttu-id="ca7f0-194">Na pasku narzędzi programu Visual Studio Zmień konfigurację kompilacji z **Debuguj** do **Release**.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-195">![Pasek narzędzi programu Visual Studio z wyróżnioną kompilacją wydania](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="ca7f0-196">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompiluj** z menu kontekstowego, aby ponownie skompilować bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="ca7f0-197">![Menu kontekstowe StringLibrary z poleceniem Build](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="ca7f0-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="ca7f0-198">Uruchom testy jednostkowe, wybierając pozycję **test Uruchom**  >  **wszystkie testy** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-198">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="ca7f0-199">Testy zostały zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-199">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ca7f0-200">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="ca7f0-200">Additional resources</span></span>

- [<span data-ttu-id="ca7f0-201">Podstawowe informacje o teście jednostkowym — Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca7f0-201">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a><span data-ttu-id="ca7f0-202">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="ca7f0-202">Next steps</span></span>

<span data-ttu-id="ca7f0-203">W tym samouczku przetestowano bibliotekę klas.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-203">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="ca7f0-204">Bibliotekę można udostępniać innym osobom, publikując ją w pakiecie [NuGet](https://nuget.org) jako pakiet.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-204">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="ca7f0-205">Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-205">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca7f0-206">Tworzenie i publikowanie pakietu NuGet przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca7f0-206">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="ca7f0-207">W przypadku opublikowania biblioteki jako pakietu NuGet inne osoby mogą ją zainstalować i używać.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-207">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="ca7f0-208">Aby dowiedzieć się, jak, postępuj zgodnie z samouczkiem NuGet:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-208">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca7f0-209">Instalowanie i używanie pakietu w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca7f0-209">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="ca7f0-210">Biblioteka nie musi być dystrybuowana jako pakiet.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-210">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="ca7f0-211">Można go powiązać z aplikacją konsolową, która go używa.</span><span class="sxs-lookup"><span data-stu-id="ca7f0-211">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="ca7f0-212">Aby dowiedzieć się, jak opublikować aplikację konsolową, zobacz wcześniejszy samouczek w tej serii:</span><span class="sxs-lookup"><span data-stu-id="ca7f0-212">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ca7f0-213">Publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca7f0-213">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
