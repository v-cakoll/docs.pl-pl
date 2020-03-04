---
title: Testowanie biblioteki klas .NET Standard przy użyciu platformy .NET Core w programie Visual Studio
description: Utwórz projekt testu jednostkowego dla biblioteki klas platformy .NET Core. Sprawdź, czy biblioteka klas .NET Core działa prawidłowo z testami jednostkowymi.
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156624"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="0b33c-104">Testowanie biblioteki .NET Standard przy użyciu platformy .NET Core w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b33c-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="0b33c-105">W obszarze [Tworzenie biblioteki .NET standard w programie Visual Studio](library-with-visual-studio.md)utworzono prostą bibliotekę klas, która dodaje metodę rozszerzenia do klasy <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="0b33c-106">Teraz utworzysz test jednostkowy, aby upewnić się, że działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="0b33c-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="0b33c-107">Należy dodać projekt testu jednostkowego do rozwiązania utworzonego w poprzednim artykule.</span><span class="sxs-lookup"><span data-stu-id="0b33c-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="0b33c-108">Tworzenie projektu testu jednostkowego</span><span class="sxs-lookup"><span data-stu-id="0b33c-108">Create a unit test project</span></span>

<span data-ttu-id="0b33c-109">Aby utworzyć projekt testu jednostkowego, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0b33c-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="0b33c-110">Otwórz rozwiązanie `ClassLibraryProjects` utworzone w [bibliotece kompilacja .NET standard w artykule Visual Studio](library-with-visual-studio.md) .</span><span class="sxs-lookup"><span data-stu-id="0b33c-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="0b33c-111">Dodaj nowy projekt testu jednostkowego o nazwie "StringLibraryTest" do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0b33c-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="0b33c-112">Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="0b33c-113">Na stronie **Dodawanie nowego projektu** wprowadź **MSTest** w polu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="0b33c-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="0b33c-114">Wybierz **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform.</span><span class="sxs-lookup"><span data-stu-id="0b33c-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="0b33c-115">Wybierz szablon **projekt testu MSTest (.NET Core)** , a następnie wybierz przycisk **dalej**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="0b33c-116">Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibraryTest** w polu **Nazwa projektu** .</span><span class="sxs-lookup"><span data-stu-id="0b33c-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="0b33c-117">Następnie wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0b33c-118">Oprócz MSTest można także tworzyć projekty testowe xUnit i nUnit dla platformy .NET Core w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0b33c-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="0b33c-119">Program Visual Studio tworzy projekt i otwiera plik klasy w oknie kodu przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="0b33c-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="0b33c-120">Kod źródłowy utworzony przez szablon testu jednostkowego wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0b33c-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="0b33c-121">Importuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> przestrzeń nazw, która zawiera typy używane do testowania jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="0b33c-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="0b33c-122">Stosuje atrybut [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) do klasy `UnitTest1`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="0b33c-123">Każda metoda testowa w klasie testowej oznaczona przy użyciu atrybutu [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) jest wykonywana automatycznie po uruchomieniu testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="0b33c-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="0b33c-124">Stosuje atrybut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) , aby zdefiniować `TestMethod1` w C# lub `TestSub` w Visual Basic jako metodę testową do automatycznego wykonania podczas działania testu jednostkowego.</span><span class="sxs-lookup"><span data-stu-id="0b33c-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="0b33c-125">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu **StringLibraryTest** i wybierz polecenie **Dodaj odwołanie** z menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="0b33c-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-126">menu kontekstowe ![zależności StringLibraryTest](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="0b33c-127">W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty** i zaznacz pole wyboru obok pozycji **StringLibrary**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="0b33c-128">Dodanie odwołania do zestawu `StringLibrary` umożliwia kompilatorowi znalezienie metod **StringLibrary** .</span><span class="sxs-lookup"><span data-stu-id="0b33c-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="0b33c-129">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-129">Select the **OK** button.</span></span> <span data-ttu-id="0b33c-130">Odwołanie jest dodawane do projektu biblioteki klas, `StringLibrary`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![Okno dialogowe programu Reference Manager w programie Visual Studio](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="0b33c-132">Dodawanie i uruchamianie metod testów jednostkowych</span><span class="sxs-lookup"><span data-stu-id="0b33c-132">Add and run unit test methods</span></span>

<span data-ttu-id="0b33c-133">Gdy program Visual Studio uruchamia test jednostkowy, wykonuje każdą metodę, która jest oznaczona atrybutem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> w klasie testów jednostkowych, klasy, do której zastosowano atrybut <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="0b33c-134">Metoda testowa kończy się po znalezieniu pierwszego błędu lub gdy wszystkie testy zawarte w metodzie zakończyły się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0b33c-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="0b33c-135">Najczęstsze testy są wywoływane przez elementy członkowskie klasy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="0b33c-136">Wiele metod Assert obejmuje co najmniej dwa parametry, z których jeden jest oczekiwany wynik testu, a drugi jest rzeczywistym wynikiem testu.</span><span class="sxs-lookup"><span data-stu-id="0b33c-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="0b33c-137">W poniższej tabeli przedstawiono niektóre z najczęściej wywoływanych metod klasy `Assert`:</span><span class="sxs-lookup"><span data-stu-id="0b33c-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="0b33c-138">Metody Assert</span><span class="sxs-lookup"><span data-stu-id="0b33c-138">Assert methods</span></span>     | <span data-ttu-id="0b33c-139">Funkcja</span><span class="sxs-lookup"><span data-stu-id="0b33c-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="0b33c-140">Sprawdza, czy dwie wartości lub obiekty są równe.</span><span class="sxs-lookup"><span data-stu-id="0b33c-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="0b33c-141">Potwierdzenie kończy się niepowodzeniem, jeśli wartości lub obiekty nie są równe.</span><span class="sxs-lookup"><span data-stu-id="0b33c-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="0b33c-142">Sprawdza, czy dwie zmienne obiektów odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b33c-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="0b33c-143">Potwierdzenie kończy się niepowodzeniem, jeśli zmienne odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0b33c-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="0b33c-144">Sprawdza, czy warunek jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="0b33c-145">Potwierdzenie kończy się niepowodzeniem, jeśli warunek jest `true`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="0b33c-146">Sprawdza, czy obiekt nie jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="0b33c-147">Potwierdzenie kończy się niepowodzeniem, jeśli obiekt jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="0b33c-148">Można również użyć metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> w metodzie testowej, aby wskazać typ wyjątku, który ma zostać zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0b33c-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="0b33c-149">Test zakończy się niepowodzeniem, jeśli określony wyjątek nie zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0b33c-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="0b33c-150">W testowaniu metody `StringLibrary.StartsWithUpper`, chcesz podać kilka ciągów zaczynających się od wielkiej litery.</span><span class="sxs-lookup"><span data-stu-id="0b33c-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="0b33c-151">Oczekujesz, aby Metoda zwracała `true` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="0b33c-152">Podobnie, chcesz podać kilka ciągów, które zaczynają się od znaku innego niż wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="0b33c-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="0b33c-153">Oczekujesz, aby Metoda zwracała `false` w takich przypadkach, aby można było wywołać metodę <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="0b33c-154">Ponieważ metoda biblioteki obsługuje ciągi, należy również upewnić się, że pomyślnie obsługuje [pusty ciąg (`String.Empty`)](xref:System.String.Empty), prawidłowy ciąg, który nie zawiera znaków i którego <xref:System.String.Length> to 0, i `null` ciąg, który nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="0b33c-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="0b33c-155">Jeśli `StartsWithUpper` jest wywoływana jako Metoda rozszerzenia w wystąpieniu <xref:System.String>, nie można przesłać ciągu `null`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="0b33c-156">Można jednak wywołać go bezpośrednio jako metodę statyczną i przekazać pojedynczy argument <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0b33c-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="0b33c-157">Zdefiniujesz trzy metody, z których każda wywołuje <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metodę wielokrotnie dla każdego elementu w tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="0b33c-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="0b33c-158">Ponieważ metoda testowa nie powiedzie się po znalezieniu pierwszego błędu, wywoła Przeciążenie metody, które umożliwia przekazywanie ciągu, który wskazuje wartość ciągu używaną w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="0b33c-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="0b33c-159">Aby utworzyć metody testowe:</span><span class="sxs-lookup"><span data-stu-id="0b33c-159">To create the test methods:</span></span>

1. <span data-ttu-id="0b33c-160">W oknie kod *UnitTest1.cs* lub *UnitTest1. vb* Zastąp kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="0b33c-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="0b33c-161">Test wielkiej litery w metodzie `TestStartsWithUpper` obejmuje wielką literę alfa (U + 0391) i wielką literę cyrylicy (U + 041C).</span><span class="sxs-lookup"><span data-stu-id="0b33c-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="0b33c-162">Test małymi literami w metodzie `TestDoesNotStartWithUpper` obejmuje małą literę alfa (U + 03B1) i małą literę cyrylicy GHE (U + 0433).</span><span class="sxs-lookup"><span data-stu-id="0b33c-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="0b33c-163">Na pasku menu wybierz pozycję **plik** > **Zapisz UnitTest1.cs jako** lub **plik** > **Zapisz UnitTest1. vb jako**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="0b33c-164">W oknie dialogowym **Zapisz plik jako** wybierz strzałkę obok przycisku **Zapisz** , a następnie wybierz pozycję **Zapisz z kodowaniem**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-165">![okna dialogowego zapisywania pliku w programie Visual Studio](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="0b33c-166">W oknie dialogowym **Potwierdzanie zapisywania jako** wybierz przycisk **tak** , aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="0b33c-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="0b33c-167">W oknie dialogowym **Zaawansowane opcje zapisywania** wybierz pozycję **Unicode (UTF-8 z podpisem)-strona kodowa 65001** z listy rozwijanej **kodowanie** i wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-168">![okno dialogowe Zaawansowane opcje zapisywania programu Visual Studio](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="0b33c-169">Jeśli kod źródłowy nie zostanie zapisany jako plik zakodowany w formacie UTF8, program Visual Studio może go zapisać jako plik ASCII.</span><span class="sxs-lookup"><span data-stu-id="0b33c-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="0b33c-170">Gdy tak się stanie, środowisko uruchomieniowe nie dekoduje znaków UTF8 poza zakresem ASCII, a wyniki testu nie będą poprawne.</span><span class="sxs-lookup"><span data-stu-id="0b33c-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="0b33c-171">Na pasku menu wybierz kolejno opcje **testuj** > **Uruchom** > **wszystkie testy**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="0b33c-172">Zostanie otwarte okno **Eksplorator testów** , które pokazuje, że testy zostały wykonane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b33c-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="0b33c-173">Trzy testy są wymienione w sekcji **testy zakończone** , a sekcja **podsumowania** raportuje wynik przebiegu testu.</span><span class="sxs-lookup"><span data-stu-id="0b33c-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-174">![okno Eksploratora testów z przekazaniem testów](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="0b33c-175">Obsługa niepowodzeń testów</span><span class="sxs-lookup"><span data-stu-id="0b33c-175">Handle test failures</span></span>

<span data-ttu-id="0b33c-176">Przebieg testu nie miał błędów, ale nieco zmienia się, tak aby jedna z metod testowych nie powiodła się:</span><span class="sxs-lookup"><span data-stu-id="0b33c-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="0b33c-177">Zmodyfikuj tablicę `words` w metodzie `TestDoesNotStartWithUpper`, aby uwzględnić ciąg "Error".</span><span class="sxs-lookup"><span data-stu-id="0b33c-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="0b33c-178">Nie musisz zapisywać pliku, ponieważ program Visual Studio automatycznie zapisuje otwarte pliki w przypadku skompilowania rozwiązania do uruchamiania testów.</span><span class="sxs-lookup"><span data-stu-id="0b33c-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="0b33c-179">Uruchom test, wybierając **test** > **Run** > **wszystkie testy** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="0b33c-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="0b33c-180">Okno **Eksplorator testów** wskazuje, że dwa testy zostały wykonane pomyślnie i jeden z nich zakończył się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0b33c-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-181">![okno Eksploratora testów z testami zakończonymi niepowodzeniem](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="0b33c-182">Wybierz test zakończony niepowodzeniem, `TestDoesNotStartWith`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="0b33c-183">W oknie **Eksplorator testów** zostanie wyświetlony komunikat utworzony przez potwierdzenie: "Assert. IsFalse nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0b33c-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="0b33c-184">Oczekiwano dla elementu "Error": false; rzeczywista: true ".</span><span class="sxs-lookup"><span data-stu-id="0b33c-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="0b33c-185">Z powodu błędu nie przetestowano wszystkich ciągów w tablicy po "błędzie".</span><span class="sxs-lookup"><span data-stu-id="0b33c-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-186">![okno Eksploratora testów przedstawiające błąd potwierdzenia IsFalse](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="0b33c-187">Cofnij modyfikację w kroku 1 i usuń ciąg "Error".</span><span class="sxs-lookup"><span data-stu-id="0b33c-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="0b33c-188">Ponownie uruchom test i testy zostaną zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b33c-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="0b33c-189">Testowanie wersji wydania biblioteki</span><span class="sxs-lookup"><span data-stu-id="0b33c-189">Test the Release version of the library</span></span>

<span data-ttu-id="0b33c-190">Uruchomiono testy w odniesieniu do wersji debugowania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0b33c-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="0b33c-191">Teraz, gdy testy zostały zakończone pomyślnie i przetestowano bibliotekę, należy uruchomić testy w dodatkowym czasie w odniesieniu do kompilacji wydania biblioteki.</span><span class="sxs-lookup"><span data-stu-id="0b33c-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="0b33c-192">Wiele czynników, w tym Optymalizacja kompilatora, może czasami generować różne zachowanie między kompilacjami w wersji Debug i Release.</span><span class="sxs-lookup"><span data-stu-id="0b33c-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="0b33c-193">Aby przetestować kompilację wydania:</span><span class="sxs-lookup"><span data-stu-id="0b33c-193">To test the Release build:</span></span>

1. <span data-ttu-id="0b33c-194">Na pasku narzędzi programu Visual Studio Zmień konfigurację kompilacji z **Debuguj** do **Release**.</span><span class="sxs-lookup"><span data-stu-id="0b33c-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-195">![pasku narzędzi programu Visual Studio z wyróżnioną kompilacją wydania](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="0b33c-196">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **StringLibrary** i wybierz polecenie **Kompiluj** z menu kontekstowego, aby ponownie skompilować bibliotekę.</span><span class="sxs-lookup"><span data-stu-id="0b33c-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="0b33c-197">![menu kontekstowe StringLibrary z poleceniem kompilacji](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="0b33c-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="0b33c-198">Uruchom testy jednostkowe, wybierając **Test** > **Run** > **wszystkie testy** z paska menu.</span><span class="sxs-lookup"><span data-stu-id="0b33c-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="0b33c-199">Testy zostały zakończone pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b33c-199">The tests pass.</span></span>

<span data-ttu-id="0b33c-200">Po zakończeniu testowania biblioteki następnym krokiem jest udostępnienie jej do wywoływania.</span><span class="sxs-lookup"><span data-stu-id="0b33c-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="0b33c-201">Można powiązać ją z co najmniej jedną lub wieloma aplikacjami lub rozpowszechniać ją jako pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0b33c-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="0b33c-202">Aby uzyskać więcej informacji, zobacz [zużywanie biblioteki klas .NET Standard](consuming-library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="0b33c-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b33c-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b33c-203">See also</span></span>

- [<span data-ttu-id="0b33c-204">Podstawowe informacje o teście jednostkowym — Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b33c-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
