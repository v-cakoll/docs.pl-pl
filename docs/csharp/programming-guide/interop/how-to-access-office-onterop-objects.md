---
title: 'Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu C# Office za C# pomocą funkcji wizualnych — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 19fff39969933baa2510458400cabf9646e0c48d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589127"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="224dd-102">Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu C# Office zaC# pomocą funkcji wizualnych (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="224dd-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="224dd-103">Wizualizacja C# zawiera funkcje, które upraszczają dostęp do obiektów interfejsu API pakietu Office.</span><span class="sxs-lookup"><span data-stu-id="224dd-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="224dd-104">Nowe funkcje obejmują argumenty nazwane i opcjonalne, nowy typ o nazwie `dynamic`oraz możliwość przekazywania argumentów do parametrów odwołań w metodach com, tak jakby były parametrami wartości.</span><span class="sxs-lookup"><span data-stu-id="224dd-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="224dd-105">W tym temacie zostaną użyte nowe funkcje do napisania kodu, który tworzy i wyświetla Microsoft Office arkusz programu Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="224dd-106">Następnie napiszesz kod, aby dodać dokument programu Office Word, który zawiera ikonę, która jest połączona z arkuszem programu Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="224dd-107">Aby ukończyć ten przewodnik, musisz mieć Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowszą wersję zainstalowanego na komputerze.</span><span class="sxs-lookup"><span data-stu-id="224dd-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="224dd-108">Aby utworzyć nową aplikację konsolową</span><span class="sxs-lookup"><span data-stu-id="224dd-108">To create a new console application</span></span>

1. <span data-ttu-id="224dd-109">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="224dd-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="224dd-110">W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="224dd-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="224dd-111">**Nowy projekt** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="224dd-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="224dd-112">W okienku **zainstalowane szablony** rozwiń pozycję **Wizualizacja C#** , a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="224dd-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="224dd-113">Sprawdź u góry okna dialogowego **Nowy projekt** , aby upewnić się, że jako platforma docelowa została wybrana wersja **.NET Framework 4** (lub nowsza).</span><span class="sxs-lookup"><span data-stu-id="224dd-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="224dd-114">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="224dd-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="224dd-115">Wpisz nazwę projektu w polu **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="224dd-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="224dd-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="224dd-116">Click **OK**.</span></span>

     <span data-ttu-id="224dd-117">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="224dd-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="224dd-118">Aby dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="224dd-118">To add references</span></span>

1. <span data-ttu-id="224dd-119">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="224dd-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="224dd-120">Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="224dd-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="224dd-121">Na stronie **zestawy** wybierz pozycję **Microsoft. Office. Interop. Word** na liście **Nazwa składnika** , a następnie przytrzymaj naciśnięty klawisz Ctrl i wybierz pozycję **Microsoft. Office. Interop. Excel**.</span><span class="sxs-lookup"><span data-stu-id="224dd-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="224dd-122">Jeśli zestawy nie są widoczne, może być konieczne zagwarantowanie, że są one zainstalowane i wyświetlone ( [zobacz How to: Instalowanie podstawowych zestawów](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)międzyoperacyjnych pakietu Office</span><span class="sxs-lookup"><span data-stu-id="224dd-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>

3. <span data-ttu-id="224dd-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="224dd-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="224dd-124">Aby dodać wymagane dyrektywy using</span><span class="sxs-lookup"><span data-stu-id="224dd-124">To add necessary using directives</span></span>

1. <span data-ttu-id="224dd-125">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik **program.cs** , a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="224dd-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="224dd-126">Dodaj następujące `using` dyrektywy na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="224dd-126">Add the following `using` directives to the top of the code file.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="224dd-127">Aby utworzyć listę kont bankowych</span><span class="sxs-lookup"><span data-stu-id="224dd-127">To create a list of bank accounts</span></span>

1. <span data-ttu-id="224dd-128">Wklej następującą definicję klasy do **program.cs**, w obszarze `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="224dd-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="224dd-129">Dodaj następujący kod do `Main` metody, aby `bankAccounts` utworzyć listę zawierającą dwa konta.</span><span class="sxs-lookup"><span data-stu-id="224dd-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="224dd-130">Aby zadeklarować metodę, która eksportuje informacje o koncie do programu Excel</span><span class="sxs-lookup"><span data-stu-id="224dd-130">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="224dd-131">Dodaj następującą metodę do klasy, `Program` aby skonfigurować arkusz programu Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="224dd-132">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma opcjonalny parametr służący do określania określonego szablonu.</span><span class="sxs-lookup"><span data-stu-id="224dd-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="224dd-133">Parametry opcjonalne, nowość w C# 4, umożliwiają pominięcie argumentu dla tego parametru, jeśli ma być używana wartość domyślna parametru.</span><span class="sxs-lookup"><span data-stu-id="224dd-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="224dd-134">Ponieważ żaden argument nie jest wysyłany w poniższym kodzie `Add` , używa szablonu domyślnego i tworzy nowy skoroszyt.</span><span class="sxs-lookup"><span data-stu-id="224dd-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="224dd-135">Równoważna instrukcja we wcześniejszych wersjach programu C# wymaga argumentu symbolu zastępczego `ExcelApp.Workbooks.Add(Type.Missing)`:.</span><span class="sxs-lookup"><span data-stu-id="224dd-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="224dd-136">Dodaj następujący kod na końcu `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="224dd-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="224dd-137">Kod wstawia wartości do pierwszych dwóch kolumn pierwszego wiersza arkusza.</span><span class="sxs-lookup"><span data-stu-id="224dd-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="224dd-138">Dodaj następujący kod na końcu `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="224dd-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="224dd-139">`foreach` Pętla umieszcza informacje z listy kont do pierwszych dwóch kolumn w kolejnych wierszach arkusza.</span><span class="sxs-lookup"><span data-stu-id="224dd-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="224dd-140">Dodaj następujący kod na końcu `DisplayInExcel` , aby dostosować szerokości kolumn w celu dopasowania do zawartości.</span><span class="sxs-lookup"><span data-stu-id="224dd-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="224dd-141">Wcześniejsze C# wersje wymagają jawnego rzutowania dla tych operacji `ExcelApp.Columns[1]` `Object`, ponieważ zwraca i `AutoFit` jest metodą programu <xref:Microsoft.Office.Interop.Excel.Range> Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="224dd-142">W poniższych wierszach przedstawiono rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="224dd-142">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="224dd-143">C#4, i nowsze wersje, konwertuje zwracaną `Object` wartość `dynamic` na automatycznie, jeśli zestaw jest przywoływany przez opcję kompilatora [/link](../../language-reference/compiler-options/link-compiler-option.md) lub, równoważne, jeśli właściwość " **Osadź typy** międzyoperacyjna programu Excel" ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="224dd-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="224dd-144">Wartość true jest wartością domyślną dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="224dd-144">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="224dd-145">Aby uruchomić projekt</span><span class="sxs-lookup"><span data-stu-id="224dd-145">To run the project</span></span>

1. <span data-ttu-id="224dd-146">Dodaj następujący wiersz na końcu `Main`.</span><span class="sxs-lookup"><span data-stu-id="224dd-146">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="224dd-147">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="224dd-147">Press CTRL+F5.</span></span>

     <span data-ttu-id="224dd-148">Zostanie wyświetlony arkusz programu Excel zawierający dane z dwóch kont.</span><span class="sxs-lookup"><span data-stu-id="224dd-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="224dd-149">Aby dodać dokument programu Word</span><span class="sxs-lookup"><span data-stu-id="224dd-149">To add a Word document</span></span>

1. <span data-ttu-id="224dd-150">Aby zilustrować dodatkowe sposoby, w których C# 4 i nowsze wersje rozszerzają Programowanie Office, poniższy kod otwiera aplikację Word i tworzy ikonę, która łączy się z arkuszem programu Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="224dd-151">Metoda `CreateIconInWordDoc`wklejenia, przedmieszczona w dalszej części tego `Program` kroku, do klasy.</span><span class="sxs-lookup"><span data-stu-id="224dd-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="224dd-152">`CreateIconInWordDoc`używa argumentów nazwanych i opcjonalnych, aby zmniejszyć złożoność wywołań metod <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> do <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>i.</span><span class="sxs-lookup"><span data-stu-id="224dd-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="224dd-153">Te wywołania obejmują dwie inne nowe funkcje wprowadzone w C# 4, które upraszczają wywołania metod com, które mają parametry referencyjne.</span><span class="sxs-lookup"><span data-stu-id="224dd-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="224dd-154">Najpierw można wysłać argumenty do parametrów odwołania, tak jakby były one parametrami wartości.</span><span class="sxs-lookup"><span data-stu-id="224dd-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="224dd-155">Oznacza to, że można wysyłać wartości bezpośrednio, bez tworzenia zmiennej dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="224dd-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="224dd-156">Kompilator generuje zmienne tymczasowe do przechowywania wartości argumentów i odrzuca zmienne po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="224dd-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="224dd-157">Następnie możesz pominąć `ref` słowo kluczowe na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="224dd-157">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="224dd-158">`Add` Metoda ma cztery parametry referencyjne, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="224dd-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="224dd-159">W C# 4,0 i nowszych wersjach można pominąć argumenty dla dowolnego lub wszystkich parametrów, jeśli chcesz użyć ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="224dd-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="224dd-160">W C# 3,0 i wcześniejszych wersjach argument musi być podany dla każdego parametru, a argument musi być zmienną, ponieważ parametry są parametrami odwołania.</span><span class="sxs-lookup"><span data-stu-id="224dd-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="224dd-161">`PasteSpecial` Metoda wstawia zawartość schowka.</span><span class="sxs-lookup"><span data-stu-id="224dd-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="224dd-162">Metoda ma siedem parametrów referencyjnych, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="224dd-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="224dd-163">Poniższy kod określa argumenty dla dwóch z nich: `Link`,, aby utworzyć łącze do źródła zawartości Schowka, i `DisplayAsIcon`, aby wyświetlić łącze jako ikonę.</span><span class="sxs-lookup"><span data-stu-id="224dd-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="224dd-164">W C# 4,0 i nowszych wersjach, można użyć nazwanych argumentów dla tych dwóch i pominąć pozostałe.</span><span class="sxs-lookup"><span data-stu-id="224dd-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="224dd-165">Chociaż są to parametry odwołania, nie trzeba używać `ref` słowa kluczowego ani do tworzenia zmiennych, które mają być wysyłane jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="224dd-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="224dd-166">Można wysłać wartości bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="224dd-166">You can send the values directly.</span></span> <span data-ttu-id="224dd-167">W C# 3,0 i wcześniejszych wersjach, należy podać zmienną argumentu dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="224dd-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="224dd-168">W C# 3,0 i wcześniejszych wersjach języka wymagany jest Poniższy kod złożony.</span><span class="sxs-lookup"><span data-stu-id="224dd-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="224dd-169">Dodaj następującą instrukcję na końcu `Main`.</span><span class="sxs-lookup"><span data-stu-id="224dd-169">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="224dd-170">Dodaj następującą instrukcję na końcu `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="224dd-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="224dd-171">`Copy` Metoda dodaje arkusz do Schowka.</span><span class="sxs-lookup"><span data-stu-id="224dd-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="224dd-172">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="224dd-172">Press CTRL+F5.</span></span>

     <span data-ttu-id="224dd-173">Zostanie wyświetlony dokument programu Word zawierający ikonę.</span><span class="sxs-lookup"><span data-stu-id="224dd-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="224dd-174">Kliknij dwukrotnie ikonę, aby przenieść arkusz na pierwszy plan.</span><span class="sxs-lookup"><span data-stu-id="224dd-174">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="224dd-175">Aby ustawić właściwość Osadź typy współdziałania</span><span class="sxs-lookup"><span data-stu-id="224dd-175">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="224dd-176">Dodatkowe ulepszenia są możliwe w przypadku wywołania typu COM, który nie wymaga podstawowego zestawu międzyoperacyjnego (PIA) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="224dd-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="224dd-177">Usunięcie zależności od zestawów Pia powoduje niezależność wersji i łatwiejsze wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="224dd-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="224dd-178">Aby uzyskać więcej informacji na temat korzyści z programowania bez zestawów Pia, [zobacz Przewodnik: Osadzanie typów z zarządzanych zestawów](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="224dd-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>

     <span data-ttu-id="224dd-179">Ponadto programowanie jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody com mogą być reprezentowane przy użyciu typu `dynamic` `Object`zamiast.</span><span class="sxs-lookup"><span data-stu-id="224dd-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="224dd-180">Zmienne o typie `dynamic` nie są oceniane do czasu uruchomienia, co eliminuje konieczność jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="224dd-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="224dd-181">Aby uzyskać więcej informacji, zobacz [Korzystanie z typu dynamicznego](../types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="224dd-181">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="224dd-182">W C# 4, osadzanie informacji o typie zamiast używania zestawów PIA jest zachowaniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="224dd-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="224dd-183">Ze względu na to, że niektóre z powyższych przykładów są uproszczone, ponieważ jawne rzutowanie nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="224dd-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="224dd-184">Na przykład deklaracja `worksheet` w programie `DisplayInExcel` jestzapisywana`Excel._Worksheet workSheet = excelApp.ActiveSheet` jako zamiast. `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`</span><span class="sxs-lookup"><span data-stu-id="224dd-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="224dd-185">Wywołania `AutoFit` w tej samej metodzie również wymagają jawnego rzutowania bez użycia domyślnego, ponieważ `ExcelApp.Columns[1]` zwraca `Object`i `AutoFit` jest metodą programu Excel.</span><span class="sxs-lookup"><span data-stu-id="224dd-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="224dd-186">Poniższy kod przedstawia rzutowanie.</span><span class="sxs-lookup"><span data-stu-id="224dd-186">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="224dd-187">Aby zmienić wartość domyślną i użyć zestawów Pia zamiast osadzania informacji o typie, rozwiń węzeł **odwołania** w **Eksplorator rozwiązań** a następnie wybierz pozycję **Microsoft. Office. Interop. Excel** lub **Microsoft. Office. Interop. Word**.</span><span class="sxs-lookup"><span data-stu-id="224dd-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="224dd-188">Jeśli nie widzisz okna **Właściwości** , naciśnij klawisz **F4**.</span><span class="sxs-lookup"><span data-stu-id="224dd-188">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="224dd-189">Znajdź **Osadź typy** międzyoperacyjności na liście właściwości i zmień jej wartość na **false**.</span><span class="sxs-lookup"><span data-stu-id="224dd-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="224dd-190">Równoważne, można skompilować przy użyciu opcji kompilatora [/Reference](../../language-reference/compiler-options/reference-compiler-option.md) zamiast [/link](../../language-reference/compiler-options/link-compiler-option.md) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="224dd-190">Equivalently, you can compile by using the [/reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="224dd-191">Aby dodać dodatkowe formatowanie do tabeli</span><span class="sxs-lookup"><span data-stu-id="224dd-191">To add additional formatting to the table</span></span>

1. <span data-ttu-id="224dd-192">Zastąp dwa wywołania `AutoFit` w programie `DisplayInExcel` , używając następującej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="224dd-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="224dd-193"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda ma siedem parametrów wartości, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="224dd-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="224dd-194">Argumenty nazwane i opcjonalne umożliwiają podanie argumentów dla braku, niektórych lub wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="224dd-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="224dd-195">W poprzedniej instrukcji argument jest dostarczany tylko dla jednego z parametrów, `Format`.</span><span class="sxs-lookup"><span data-stu-id="224dd-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="224dd-196">Ponieważ `Format` jest pierwszym parametrem na liście parametrów, nie trzeba podawać nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="224dd-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="224dd-197">Jednak instrukcja może być łatwiejsza do zrozumienia, jeśli nazwa parametru jest uwzględniona, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="224dd-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="224dd-198">Naciśnij klawisze CTRL + F5, aby zobaczyć wynik.</span><span class="sxs-lookup"><span data-stu-id="224dd-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="224dd-199">Inne formaty są wymienione w <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="224dd-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="224dd-200">Porównaj instrukcję w kroku 1 z poniższym kodem, który pokazuje argumenty wymagane w C# 3,0 i wcześniejszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="224dd-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="224dd-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="224dd-201">Example</span></span>

<span data-ttu-id="224dd-202">Poniższy kod przedstawia kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="224dd-202">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="224dd-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="224dd-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="224dd-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="224dd-204">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="224dd-205">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="224dd-205">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="224dd-206">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="224dd-206">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="224dd-207">Instrukcje: Używanie argumentów nazwanych i opcjonalnych w programowaniu pakietu Office</span><span class="sxs-lookup"><span data-stu-id="224dd-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
