---
title: Jak uzyskać dostęp do obiektów pakietu Office interop - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: b5d2da011ec6318c8b07f1eb4d383a4d56488239
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700838"
---
# <a name="how-to-access-office-interop-objects-c-programming-guide"></a><span data-ttu-id="07eef-102">Jak uzyskać dostęp do obiektów pakietu Office interop (Przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="07eef-102">How to access Office interop objects (C# Programming Guide)</span></span>

<span data-ttu-id="07eef-103">Język C# ma funkcje, które upraszczają dostęp do obiektów interfejsu API pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="07eef-103">C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="07eef-104">Nowe funkcje obejmują nazwane i opcjonalne `dynamic`argumenty, nowy typ o nazwie i możliwość przekazywania argumentów do parametrów referencyjnych w metodach COM, tak jakby były parametrami wartości.</span><span class="sxs-lookup"><span data-stu-id="07eef-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="07eef-105">W tym temacie użyjesz nowych funkcji do pisania kodu, który tworzy i wyświetla arkusz programu Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="07eef-106">Następnie napiszesz kod, aby dodać dokument programu Office Word zawierający ikonę połączoną z arkuszem programu Excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="07eef-107">Aby wypełnić ten instruktaż, na komputerze muszą być zainstalowane programy Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="07eef-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="07eef-108">Aby utworzyć nową aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="07eef-108">To create a new console application</span></span>

1. <span data-ttu-id="07eef-109">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07eef-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="07eef-110">W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="07eef-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="07eef-111">Zostanie wyświetlone okno dialogowe **Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="07eef-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="07eef-112">W okienku **Zainstalowane szablony** rozwiń węzeł **Visual C#,** a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="07eef-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="07eef-113">Spójrz na górze okna dialogowego **Nowy projekt,** aby upewnić się, że **.NET Framework 4** (lub nowsza wersja) jest wybrany jako platforma docelowa.</span><span class="sxs-lookup"><span data-stu-id="07eef-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="07eef-114">W okienku **Szablony** kliknij pozycję **Aplikacja konsoli**.</span><span class="sxs-lookup"><span data-stu-id="07eef-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="07eef-115">Wpisz nazwę projektu w polu **Nazwa.**</span><span class="sxs-lookup"><span data-stu-id="07eef-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="07eef-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="07eef-116">Click **OK**.</span></span>

     <span data-ttu-id="07eef-117">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="07eef-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="07eef-118">Aby dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="07eef-118">To add references</span></span>

1. <span data-ttu-id="07eef-119">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="07eef-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="07eef-120">Pojawi się okno dialogowe **Dodawanie odwołania.**</span><span class="sxs-lookup"><span data-stu-id="07eef-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="07eef-121">Na stronie **Zestawy** wybierz pozycję **Microsoft.Office.Interop.Word** na liście **Nazwa składnika,** a następnie przytrzymaj naciśnięty klawisz CTRL i wybierz pozycję **Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="07eef-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="07eef-122">Jeśli nie widzisz zestawów, może być konieczne upewnienie się, że są one zainstalowane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="07eef-122">If you do not see the assemblies, you may need to ensure they are installed and displayed.</span></span> <span data-ttu-id="07eef-123">Zobacz [jak: Instalowanie podstawowych zestawów interop pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span><span class="sxs-lookup"><span data-stu-id="07eef-123">See [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies).</span></span>

3. <span data-ttu-id="07eef-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="07eef-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="07eef-125">Aby dodać niezbędne za pomocą dyrektyw</span><span class="sxs-lookup"><span data-stu-id="07eef-125">To add necessary using directives</span></span>

1. <span data-ttu-id="07eef-126">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Program.cs,* a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="07eef-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="07eef-127">Dodaj następujące `using` dyrektywy do górnej części pliku kodu:</span><span class="sxs-lookup"><span data-stu-id="07eef-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="07eef-128">Aby utworzyć listę kont bankowych</span><span class="sxs-lookup"><span data-stu-id="07eef-128">To create a list of bank accounts</span></span>

1. <span data-ttu-id="07eef-129">Wklej następującą **Program.cs**definicję klasy `Program` do Program.cs , w klasie.</span><span class="sxs-lookup"><span data-stu-id="07eef-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="07eef-130">Dodaj następujący kod `Main` do metody, `bankAccounts` aby utworzyć listę zawierającą dwa konta.</span><span class="sxs-lookup"><span data-stu-id="07eef-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="07eef-131">Aby zadeklarować metodę eksportuzią informacje o koncie do programu Excel</span><span class="sxs-lookup"><span data-stu-id="07eef-131">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="07eef-132">Dodaj następującą `Program` metodę do klasy, aby skonfigurować arkusz programu Excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="07eef-133">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma opcjonalny parametr do określania określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="07eef-133">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="07eef-134">Parametry opcjonalne, nowe w języku C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru.</span><span class="sxs-lookup"><span data-stu-id="07eef-134">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="07eef-135">Ponieważ żaden argument nie jest `Add` wysyłany w następującym kodzie, używa szablonu domyślnego i tworzy nowy skoroszyt.</span><span class="sxs-lookup"><span data-stu-id="07eef-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="07eef-136">Równoważna instrukcja we wcześniejszych wersjach języka `ExcelApp.Workbooks.Add(Type.Missing)`C# wymaga argumentu zastępczego: .</span><span class="sxs-lookup"><span data-stu-id="07eef-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="07eef-137">Dodaj następujący kod na `DisplayInExcel`końcu pliku .</span><span class="sxs-lookup"><span data-stu-id="07eef-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="07eef-138">Kod wstawia wartości do pierwszych dwóch kolumn pierwszego wiersza arkusza.</span><span class="sxs-lookup"><span data-stu-id="07eef-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="07eef-139">Dodaj następujący kod na `DisplayInExcel`końcu pliku .</span><span class="sxs-lookup"><span data-stu-id="07eef-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="07eef-140">Pętla `foreach` umieszcza informacje z listy kont w pierwszych dwóch kolumnach kolejnych wierszy arkusza.</span><span class="sxs-lookup"><span data-stu-id="07eef-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="07eef-141">Dodaj następujący kod na `DisplayInExcel` końcu, aby dostosować szerokość kolumn, aby dopasować ją do zawartości.</span><span class="sxs-lookup"><span data-stu-id="07eef-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="07eef-142">Wcześniejsze wersje języka C# wymagają jawnego `Object`rzutowania `AutoFit` dla <xref:Microsoft.Office.Interop.Excel.Range> tych operacji, ponieważ `ExcelApp.Columns[1]` zwraca metodę programu Excel i jest metodą programu Excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="07eef-143">W poniższych wierszach przedstawiono rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="07eef-143">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="07eef-144">C# 4 i nowsze wersje `Object` `dynamic` konwertuje zwracane do automatycznie, jeśli zestaw odwołuje się do opcji kompilatora [-link](../../language-reference/compiler-options/link-compiler-option.md) lub, podobnie, jeśli program Excel **Embed Interop Types** właściwość jest ustawiona na true.</span><span class="sxs-lookup"><span data-stu-id="07eef-144">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [-link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="07eef-145">Wartość True jest wartością domyślną dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="07eef-145">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="07eef-146">Aby uruchomić projekt</span><span class="sxs-lookup"><span data-stu-id="07eef-146">To run the project</span></span>

1. <span data-ttu-id="07eef-147">Dodaj następujący wiersz na `Main`końcu .</span><span class="sxs-lookup"><span data-stu-id="07eef-147">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="07eef-148">Naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="07eef-148">Press CTRL+F5.</span></span>

     <span data-ttu-id="07eef-149">Pojawi się arkusz programu Excel zawierający dane z dwóch kont.</span><span class="sxs-lookup"><span data-stu-id="07eef-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="07eef-150">Aby dodać dokument programu Word</span><span class="sxs-lookup"><span data-stu-id="07eef-150">To add a Word document</span></span>

1. <span data-ttu-id="07eef-151">Aby zilustrować dodatkowe sposoby, w których C# 4 i nowsze wersje, zwiększa programowanie pakietu Office, poniższy kod otwiera aplikację programu Word i tworzy ikonę, która łączy się z arkuszem programu Excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-151">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="07eef-152">Wklej `CreateIconInWordDoc`metodę , pod warunkiem, `Program` że w dalszej części tego kroku, do klasy.</span><span class="sxs-lookup"><span data-stu-id="07eef-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="07eef-153">`CreateIconInWordDoc`używa nazwanych i opcjonalnych argumentów, aby <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>zmniejszyć złożoność wywołań metody i .</span><span class="sxs-lookup"><span data-stu-id="07eef-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="07eef-154">Te wywołania zawierają dwie inne nowe funkcje wprowadzone w języku C# 4, które upraszczają wywołania metod COM, które mają parametry referencyjne.</span><span class="sxs-lookup"><span data-stu-id="07eef-154">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="07eef-155">Najpierw można wysyłać argumenty do parametrów odwołania tak, jakby były parametrami wartości.</span><span class="sxs-lookup"><span data-stu-id="07eef-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="07eef-156">Oznacza to, że można wysyłać wartości bezpośrednio, bez tworzenia zmiennej dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="07eef-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="07eef-157">Kompilator generuje zmienne tymczasowe do przechowywania wartości argumentu i odrzuca zmienne po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="07eef-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="07eef-158">Po drugie, można `ref` pominąć słowo kluczowe na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="07eef-158">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="07eef-159">Metoda `Add` ma cztery parametry referencyjne, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="07eef-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="07eef-160">W wersji C# 4.0 i nowszych można pominąć argumenty dla dowolnego lub wszystkich parametrów, jeśli chcesz użyć ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="07eef-160">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="07eef-161">W języku C# 3.0 i wcześniejszych wersjach należy podać argument dla każdego parametru, a argument musi być zmienna, ponieważ parametry są parametrami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="07eef-161">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="07eef-162">Metoda `PasteSpecial` wstawia zawartość Schowka.</span><span class="sxs-lookup"><span data-stu-id="07eef-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="07eef-163">Metoda ma siedem parametrów referencyjnych, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="07eef-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="07eef-164">Poniższy kod określa argumenty dla `Link`dwóch z nich: , aby utworzyć łącze do `DisplayAsIcon`źródła zawartości Schowka i , aby wyświetlić łącze jako ikonę.</span><span class="sxs-lookup"><span data-stu-id="07eef-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="07eef-165">W wersji C# 4.0 i nowszych można użyć nazwanych argumentów dla tych dwóch i pominąć inne.</span><span class="sxs-lookup"><span data-stu-id="07eef-165">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="07eef-166">Chociaż są to parametry referencyjne, nie `ref` trzeba używać słowa kluczowego ani tworzyć zmiennych do wysyłania jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="07eef-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="07eef-167">Wartości można wysyłać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="07eef-167">You can send the values directly.</span></span> <span data-ttu-id="07eef-168">W języku C# 3.0 i wcześniejszych wersjach należy podać argument zmiennej dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="07eef-168">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="07eef-169">W języku C# 3.0 i wcześniejszych wersjach języka wymagany jest następujący bardziej złożony kod.</span><span class="sxs-lookup"><span data-stu-id="07eef-169">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="07eef-170">Dodaj następującą instrukcję `Main`na końcu .</span><span class="sxs-lookup"><span data-stu-id="07eef-170">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="07eef-171">Dodaj następującą instrukcję `DisplayInExcel`na końcu .</span><span class="sxs-lookup"><span data-stu-id="07eef-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="07eef-172">Metoda `Copy` dodaje arkusz do Schowka.</span><span class="sxs-lookup"><span data-stu-id="07eef-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="07eef-173">Naciśnij klawisze CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="07eef-173">Press CTRL+F5.</span></span>

     <span data-ttu-id="07eef-174">Zostanie wyświetlony dokument programu Word zawierający ikonę.</span><span class="sxs-lookup"><span data-stu-id="07eef-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="07eef-175">Kliknij dwukrotnie ikonę, aby przenieść arkusz na pierwszy plan.</span><span class="sxs-lookup"><span data-stu-id="07eef-175">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="07eef-176">Aby ustawić właściwość Embed Interop Types</span><span class="sxs-lookup"><span data-stu-id="07eef-176">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="07eef-177">Dodatkowe ulepszenia są możliwe podczas wywoływania typu COM, który nie wymaga podstawowego zestawu współrzędnego (PIA) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="07eef-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="07eef-178">Usunięcie zależności od pias powoduje niezależność wersji i łatwiejsze wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="07eef-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="07eef-179">Aby uzyskać więcej informacji na temat zalet programowania bez pias, zobacz [Instruktaż: Osadzanie typów z zestawów zarządzanych](../../../standard/assembly/embed-types-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="07eef-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="07eef-180">Ponadto programowanie jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody `dynamic` COM `Object`mogą być reprezentowane przy użyciu typu zamiast .</span><span class="sxs-lookup"><span data-stu-id="07eef-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="07eef-181">Zmienne, które `dynamic` mają typ nie są oceniane do czasu wykonywania, co eliminuje potrzebę jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="07eef-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="07eef-182">Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji Typ dynamiczny](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="07eef-182">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="07eef-183">W języku C# 4 osadzanie informacji o typie zamiast używania pias jest zachowaniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="07eef-183">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="07eef-184">Ze względu na to ustawienie domyślne kilka poprzednich przykładów są uproszczone, ponieważ jawne rzutowanie nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="07eef-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="07eef-185">Na przykład deklaracja `worksheet` `DisplayInExcel` w jest `Excel._Worksheet workSheet = excelApp.ActiveSheet` zapisywana jako , a nie `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="07eef-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="07eef-186">Wywołania `AutoFit` w tej samej metodzie również wymagałoby `ExcelApp.Columns[1]` jawnego `Object`rzutowania bez domyślnego, ponieważ zwraca , i `AutoFit` jest metodą excel.</span><span class="sxs-lookup"><span data-stu-id="07eef-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="07eef-187">Poniższy kod pokazuje rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="07eef-187">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="07eef-188">Aby zmienić domyślne i używać piAs zamiast osadzania informacji o typie, rozwiń węzeł **Odwołania** w **Eksploratorze rozwiązań,** a następnie wybierz pozycję **Microsoft.Office.Interop.Excel** lub **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="07eef-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="07eef-189">Jeśli nie widzisz okna **Właściwości,** naciśnij klawisz **F4**.</span><span class="sxs-lookup"><span data-stu-id="07eef-189">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="07eef-190">Znajdź **embed Interop Types** na liście właściwości i zmień jego wartość na **False**.</span><span class="sxs-lookup"><span data-stu-id="07eef-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="07eef-191">Podobnie można skompilować przy użyciu opcji [kompilatora -reference](../../language-reference/compiler-options/reference-compiler-option.md) zamiast [-link](../../language-reference/compiler-options/link-compiler-option.md) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="07eef-191">Equivalently, you can compile by using the [-reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [-link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="07eef-192">Aby dodać dodatkowe formatowanie do tabeli</span><span class="sxs-lookup"><span data-stu-id="07eef-192">To add additional formatting to the table</span></span>

1. <span data-ttu-id="07eef-193">Zastąp `AutoFit` dwa `DisplayInExcel` wywołania w następującej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="07eef-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="07eef-194">Metoda <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> ma siedem parametrów wartości, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="07eef-194">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="07eef-195">Nazwane i opcjonalne argumenty umożliwiają podanie argumentów dla żadnego, niektórych lub wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="07eef-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="07eef-196">W poprzedniej instrukcji argument jest dostarczany tylko dla jednego `Format`z parametrów.</span><span class="sxs-lookup"><span data-stu-id="07eef-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="07eef-197">Ponieważ `Format` jest to pierwszy parametr na liście parametrów, nie trzeba podawać nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="07eef-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="07eef-198">Jednak instrukcja może być łatwiejsze do zrozumienia, jeśli nazwa parametru jest dodany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07eef-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="07eef-199">Naciśnij klawisze CTRL+F5, aby zobaczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="07eef-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="07eef-200">Inne formaty są wymienione <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="07eef-200">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="07eef-201">Porównaj instrukcję w kroku 1 z następującym kodem, który pokazuje argumenty, które są wymagane w języku C# 3.0 i wcześniejszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="07eef-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="07eef-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="07eef-202">Example</span></span>

<span data-ttu-id="07eef-203">Poniższy kod przedstawia pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="07eef-203">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="07eef-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07eef-204">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="07eef-205">Dynamiczne</span><span class="sxs-lookup"><span data-stu-id="07eef-205">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="07eef-206">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="07eef-206">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="07eef-207">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="07eef-207">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="07eef-208">Porada: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office</span><span class="sxs-lookup"><span data-stu-id="07eef-208">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
