---
title: Testowanie biblioteki klas .NET Standard z .NET Core w programie Visual Studio
description: Utwórz projekt testu jednostkowego dla biblioteki klas .NET Core. Sprawdź, czy biblioteka klas .NET Core działa poprawnie z testami jednostkowym.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156624"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="365f8-104">Testowanie biblioteki standardu .NET z .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="365f8-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="365f8-105">W [tworzenie biblioteki .NET Standard w programie Visual Studio](library-with-visual-studio.md)utworzono prostą <xref:System.String> bibliotekę klas, która dodaje metodę rozszerzenia do klasy.</span><span class="sxs-lookup"><span data-stu-id="365f8-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="365f8-106">Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="365f8-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="365f8-107">Dodasz projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.</span><span class="sxs-lookup"><span data-stu-id="365f8-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="365f8-108">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="365f8-108">Create a unit test project</span></span>

<span data-ttu-id="365f8-109">Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="365f8-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="365f8-110">Otwórz `ClassLibraryProjects` rozwiązanie utworzone w artykule [Tworzenie biblioteki standardu .NET w](library-with-visual-studio.md) programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="365f8-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="365f8-111">Dodaj nowy projekt testu jednostkowego o nazwie "StringLibraryTest" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="365f8-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="365f8-112">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="365f8-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="365f8-113">Na stronie **Dodaj nowy projekt** wprowadź **mstest** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="365f8-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="365f8-114">Wybierz **c#** lub **Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma.</span><span class="sxs-lookup"><span data-stu-id="365f8-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="365f8-115">Wybierz szablon **Projektu testowego Programu MsTest (.NET Core),** a następnie wybierz pozycję **Dalej**.</span><span class="sxs-lookup"><span data-stu-id="365f8-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="365f8-116">Na stronie **Konfigurowanie nowego projektu** wprowadź **ciąg StringLibraryTest** w polu **Nazwa projektu.**</span><span class="sxs-lookup"><span data-stu-id="365f8-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="365f8-117">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="365f8-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="365f8-118">Oprócz mstest, można również utworzyć xUnit i nUnit projektów testowych dla .NET Core w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="365f8-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="365f8-119">Program Visual Studio tworzy projekt i otwiera plik klasy w oknie kodu z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="365f8-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="365f8-120">Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="365f8-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="365f8-121">Importuje obszar <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> nazw, który zawiera typy używane do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="365f8-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="365f8-122">Stosuje [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) atrybut do `UnitTest1` klasy.</span><span class="sxs-lookup"><span data-stu-id="365f8-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="365f8-123">Każda metoda testowa w klasie testowej oznaczona atrybutem [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) jest wykonywana automatycznie po uruchomieniu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="365f8-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="365f8-124">Stosuje [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) atrybut do `TestMethod1` definiowania `TestSub` w języku C# lub w języku Visual Basic jako metoda testowa do automatycznego wykonywania po uruchomieniu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="365f8-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="365f8-125">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="365f8-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-126">![Menu kontekstowe zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="365f8-127">W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **Projekty** i zaznacz pole wyboru obok **pozycji StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="365f8-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="365f8-128">Dodanie odwołania do `StringLibrary` zestawu umożliwia kompilatorowi znajdowanie metod **StringLibrary.**</span><span class="sxs-lookup"><span data-stu-id="365f8-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="365f8-129">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="365f8-129">Select the **OK** button.</span></span> <span data-ttu-id="365f8-130">Odwołanie zostanie dodane do projektu `StringLibrary`biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="365f8-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Okno dialogowe Menedżera odwołań w programie Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="365f8-132">Dodawanie i uruchamianie metod testowania jednostkowego</span><span class="sxs-lookup"><span data-stu-id="365f8-132">Add and run unit test methods</span></span>

<span data-ttu-id="365f8-133">Gdy program Visual Studio uruchamia test jednostkowy, wykonuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> każdą metodę, która jest oznaczona atrybutem w klasie testu jednostkowego, klasy, do której jest stosowany <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="365f8-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="365f8-134">Metoda testowa kończy się, gdy zostanie znaleziony pierwszy błąd lub gdy wszystkie testy zawarte w metodzie zakończyły się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="365f8-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="365f8-135">Najczęstsze testy wywołać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> członków klasy.</span><span class="sxs-lookup"><span data-stu-id="365f8-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="365f8-136">Wiele metod potwierdzenia obejmują co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywisty wynik testu.</span><span class="sxs-lookup"><span data-stu-id="365f8-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="365f8-137">Niektóre z `Assert` najczęściej wywoływanych metod klasy przedstawiono w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="365f8-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="365f8-138">Metody potwierdzania</span><span class="sxs-lookup"><span data-stu-id="365f8-138">Assert methods</span></span>     | <span data-ttu-id="365f8-139">Funkcja</span><span class="sxs-lookup"><span data-stu-id="365f8-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="365f8-140">Sprawdza, czy dwie wartości lub obiekty są równe.</span><span class="sxs-lookup"><span data-stu-id="365f8-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="365f8-141">Assert nie powiedzie się, jeśli wartości lub obiekty nie są równe.</span><span class="sxs-lookup"><span data-stu-id="365f8-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="365f8-142">Sprawdza, czy dwie zmienne obiektu odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="365f8-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="365f8-143">Assert nie powiedzie się, jeśli zmienne odnoszą się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="365f8-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="365f8-144">Sprawdza, czy warunek `false`jest .</span><span class="sxs-lookup"><span data-stu-id="365f8-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="365f8-145">Potwierdzenie nie powiedzie `true`się, jeśli warunek jest .</span><span class="sxs-lookup"><span data-stu-id="365f8-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="365f8-146">Sprawdza, czy obiekt nie `null`jest .</span><span class="sxs-lookup"><span data-stu-id="365f8-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="365f8-147">Assert nie powiedzie `null`się, jeśli obiekt jest .</span><span class="sxs-lookup"><span data-stu-id="365f8-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="365f8-148">Można również użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metody w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="365f8-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="365f8-149">Test nie powiedzie się, jeśli określony wyjątek nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="365f8-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="365f8-150">Podczas testowania `StringLibrary.StartsWithUpper` metody chcesz podać liczbę ciągów, które zaczynają się wielkimi literami.</span><span class="sxs-lookup"><span data-stu-id="365f8-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="365f8-151">Można oczekiwać, `true` że metoda do zwrócenia <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> w tych przypadkach, dzięki czemu można wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="365f8-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="365f8-152">Podobnie chcesz podać szereg ciągów, które zaczynają się od czegoś innego niż wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="365f8-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="365f8-153">Można oczekiwać, `false` że metoda do zwrócenia <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> w tych przypadkach, dzięki czemu można wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="365f8-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="365f8-154">Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie ma znaków i którego <xref:System.String.Length> jest 0, oraz `null` ciąg, który nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="365f8-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="365f8-155">Jeśli `StartsWithUpper` jest wywoływana jako <xref:System.String> metoda rozszerzenia w wystąpieniu, `null` nie można przekazać ciąg.</span><span class="sxs-lookup"><span data-stu-id="365f8-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="365f8-156">Można jednak również wywołać go bezpośrednio jako metodę <xref:System.String> statyczną i przekazać pojedynczy argument.</span><span class="sxs-lookup"><span data-stu-id="365f8-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="365f8-157">Zdefiniujesz trzy metody, z których <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> każda wywołuje metodę wielokrotnie dla każdego elementu w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="365f8-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="365f8-158">Ponieważ metoda testowa kończy się niepowodzeniem, gdy tylko znajdzie pierwszy błąd, wywołasz przeciążenie metody, które umożliwia przekazanie ciągu, który wskazuje wartość ciągu używanew wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="365f8-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="365f8-159">Aby utworzyć metody testowe:</span><span class="sxs-lookup"><span data-stu-id="365f8-159">To create the test methods:</span></span>

1. <span data-ttu-id="365f8-160">W oknie kodu *UnitTest1.cs* lub *UnitTest1.vb* zastąp kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="365f8-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="365f8-161">Test wielkich liter w `TestStartsWithUpper` metodzie obejmuje grecką literę alfa (U+0391) i literę cyrylicy EM (U+041C).</span><span class="sxs-lookup"><span data-stu-id="365f8-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="365f8-162">Test małych liter w `TestDoesNotStartWithUpper` metodzie obejmuje grecką małą literę alfa (U +03B1) i cyrylica małą literę Ghe (U +0433).</span><span class="sxs-lookup"><span data-stu-id="365f8-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="365f8-163">Na pasku menu wybierz pozycję**Zapisz UnitTest1.cs jako** **pliku** > lub **Zapisz plik** > **UnitTest1.vb Jako**.</span><span class="sxs-lookup"><span data-stu-id="365f8-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="365f8-164">W oknie dialogowym **Zapisywanie pliku jako** zaznacz strzałkę obok przycisku **Zapisz** i wybierz pozycję Zapisz za **pomocą kodowania**.</span><span class="sxs-lookup"><span data-stu-id="365f8-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-165">![Okno dialogowe Zapisywanie pliku w programie Visual Studio jako](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="365f8-166">W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **Tak,** aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="365f8-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="365f8-167">W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem) — strona kodowa 65001** z listy rozwijanej **Kodowanie** i wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="365f8-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-168">![Okno dialogowe Zaawansowane opcje zapisywania programu Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="365f8-169">Jeśli nie uda się zapisać kodu źródłowego jako pliku zakodowanego w utf8, program Visual Studio może zapisać go jako plik ASCII.</span><span class="sxs-lookup"><span data-stu-id="365f8-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="365f8-170">W takim przypadku program runtime nie dokładnie dekoduje znaki UTF8 poza zakresem ASCII, a wyniki testu nie będą poprawne.</span><span class="sxs-lookup"><span data-stu-id="365f8-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="365f8-171">Na pasku menu wybierz **opcję Uruchom** > **testuj** > **wszystkie testy**.</span><span class="sxs-lookup"><span data-stu-id="365f8-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="365f8-172">Okno **Eksploratora testów** zostanie otwarte i pokaże, że testy zostały pomyślnie przeprowadzone.</span><span class="sxs-lookup"><span data-stu-id="365f8-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="365f8-173">Trzy testy są wymienione w **sekcji Zdany testy,** a sekcja **Podsumowanie** zgłasza wynik przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="365f8-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-174">![Okno Eksploratora testów z testami zaliczenia](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="365f8-175">Obsługa błędów testów</span><span class="sxs-lookup"><span data-stu-id="365f8-175">Handle test failures</span></span>

<span data-ttu-id="365f8-176">Przebieg testowy nie miał żadnych błędów, ale zmień go nieznacznie, aby jedna z metod testowych nie powiodła się:</span><span class="sxs-lookup"><span data-stu-id="365f8-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="365f8-177">Zmodyfikuj tablicę `words` w metodzie, `TestDoesNotStartWithUpper` aby uwzględnić ciąg "Błąd".</span><span class="sxs-lookup"><span data-stu-id="365f8-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="365f8-178">Nie trzeba zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki, gdy rozwiązanie jest zbudowane do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="365f8-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="365f8-179">Uruchom test, wybierając **opcję Uruchom test** > **Run** > **wszystkie testy** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="365f8-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="365f8-180">Okno **Eksploratora testów** wskazuje, że dwa testy zakończyły się pomyślnie, a jeden zakończył się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="365f8-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-181">![Okno Eksploratora testów z nieudanym testem](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="365f8-182">Wybierz nieudany `TestDoesNotStartWith`test .</span><span class="sxs-lookup"><span data-stu-id="365f8-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="365f8-183">W oknie **Eksploratora testów** jest wyświetlany komunikat wyprodukowany przez assert: "Assert.IsFalse nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="365f8-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="365f8-184">Oczekiwano dla "Błąd": false; rzeczywiste: Prawda".</span><span class="sxs-lookup"><span data-stu-id="365f8-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="365f8-185">Z powodu awarii wszystkie ciągi w tablicy po "Błąd" nie zostały przetestowane.</span><span class="sxs-lookup"><span data-stu-id="365f8-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-186">![Okno Eksploratora testów z błędem potwierdzenia IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="365f8-187">Cofnij modyfikację, którą wykonałeś w kroku 1 i usuń ciąg "Błąd".</span><span class="sxs-lookup"><span data-stu-id="365f8-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="365f8-188">Uruchom ponownie test, a testy przejdą.</span><span class="sxs-lookup"><span data-stu-id="365f8-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="365f8-189">Testowanie wersji biblioteki</span><span class="sxs-lookup"><span data-stu-id="365f8-189">Test the Release version of the library</span></span>

<span data-ttu-id="365f8-190">Zostały uruchomione testy przeciwko debugwersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="365f8-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="365f8-191">Teraz, gdy wszystkie testy zostały zadane i zostały odpowiednio przetestowane biblioteki, należy uruchomić testy dodatkowy czas przed release kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="365f8-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="365f8-192">Wiele czynników, w tym optymalizacji kompilatora, czasami może powodować różne zachowanie między kompilacjami debugowania i wydania.</span><span class="sxs-lookup"><span data-stu-id="365f8-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="365f8-193">Aby przetestować kompilację wersji:</span><span class="sxs-lookup"><span data-stu-id="365f8-193">To test the Release build:</span></span>

1. <span data-ttu-id="365f8-194">Na pasku narzędzi programu Visual Studio zmień konfigurację kompilacji z **Debug** na **Release**.</span><span class="sxs-lookup"><span data-stu-id="365f8-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-195">![Pasek narzędzi programu Visual Studio z wyróżnioną kompilacją wersji](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="365f8-196">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompilacja** z menu kontekstowego, aby ponownie skompilować bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="365f8-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="365f8-197">![Menu kontekstowe StringLibrary z poleceniem kompilacji](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="365f8-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="365f8-198">Uruchom testy jednostkowe, wybierając z paska menu opcję **Uruchom próbę** > **Run** > **wszystkie testy.**</span><span class="sxs-lookup"><span data-stu-id="365f8-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="365f8-199">Testy zaprzechodzą.</span><span class="sxs-lookup"><span data-stu-id="365f8-199">The tests pass.</span></span>

<span data-ttu-id="365f8-200">Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej wywołującym.</span><span class="sxs-lookup"><span data-stu-id="365f8-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="365f8-201">Można połączyć go z jedną lub więcej aplikacji lub można rozpowszechniać go jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="365f8-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="365f8-202">Aby uzyskać więcej informacji, zobacz [Korzystanie ze standardowej biblioteki klas .NET](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="365f8-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="365f8-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="365f8-203">See also</span></span>

- [<span data-ttu-id="365f8-204">Podstawowe informacje o testach jednostkowych — Visual Studio</span><span class="sxs-lookup"><span data-stu-id="365f8-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
