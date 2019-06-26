---
title: 'Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcje — C# przewodnik programowania'
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
ms.openlocfilehash: 765a150953075cf9afb2dd3bde7a66cfe3ff6eb5
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398158"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="624a3-102">Instrukcje: Dostęp do obiektów międzyoperacyjności pakietu Office przy użyciu Visual C# funkcji (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="624a3-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="624a3-103">Visual C# zawiera funkcje, które ułatwiają dostęp do obiektów interfejsu API usługi Office.</span><span class="sxs-lookup"><span data-stu-id="624a3-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="624a3-104">Nowe funkcje obejmują argumentów nazwanych i opcjonalnych, nowy typ o nazwie `dynamic`oraz możliwość przekazywania argumentów do parametrów odwołania w metodach COM tak, jakby były one wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="624a3-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="624a3-105">W tym temacie użyjesz nowych funkcji do pisania kodu, które tworzy i wyświetla arkusz programu Microsoft Office Excel.</span><span class="sxs-lookup"><span data-stu-id="624a3-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="624a3-106">Następnie napiszesz kod, aby dodać dokument programu Word pakietu Office, który zawiera ikonę która jest połączona w arkuszu programu Excel.</span><span class="sxs-lookup"><span data-stu-id="624a3-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="624a3-107">Do przeprowadzenia tego instruktażu, musi mieć Microsoft Office Excel 2007 i Microsoft Office Word 2007 lub nowszy zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="624a3-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="624a3-108">Aby utworzyć nową aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="624a3-108">To create a new console application</span></span>

1. <span data-ttu-id="624a3-109">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="624a3-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="624a3-110">Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="624a3-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="624a3-111">**Nowy projekt** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="624a3-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="624a3-112">W **zainstalowane szablony** okienku rozwiń **Visual C#** , a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="624a3-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="624a3-113">Szukaj w górnej części **nowy projekt** upewnij się, że okno dialogowe **.NET Framework 4** (lub nowsza wersja) został wybrany jako platforma docelowa.</span><span class="sxs-lookup"><span data-stu-id="624a3-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="624a3-114">W **szablony** okienku kliknij **aplikację Konsolową**.</span><span class="sxs-lookup"><span data-stu-id="624a3-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="624a3-115">Wpisz nazwę dla projektu w **nazwa** pola.</span><span class="sxs-lookup"><span data-stu-id="624a3-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="624a3-116">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="624a3-116">Click **OK**.</span></span>

     <span data-ttu-id="624a3-117">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="624a3-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="624a3-118">Aby dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="624a3-118">To add references</span></span>

1. <span data-ttu-id="624a3-119">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="624a3-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="624a3-120">**Dodaj odwołanie** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="624a3-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="624a3-121">Na **zestawy** wybierz opcję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy, a następnie przytrzymaj naciśnięty klawisz CTRL, klucza i wybierz pozycję  **Microsoft.Office.Interop.Excel**.</span><span class="sxs-lookup"><span data-stu-id="624a3-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="624a3-122">Jeśli nie ma zestawów, może być konieczne upewnić się, są zainstalowane i wyświetlane (zobacz [jak: Instalowanie podstawowych zestawów międzyoperacyjnych pakietu Office](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span><span class="sxs-lookup"><span data-stu-id="624a3-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>

3. <span data-ttu-id="624a3-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="624a3-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="624a3-124">Aby dodać niezbędne dyrektyw using</span><span class="sxs-lookup"><span data-stu-id="624a3-124">To add necessary using directives</span></span>

1. <span data-ttu-id="624a3-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="624a3-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="624a3-126">Dodaj następujący kod `using` dyrektywy na górze pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="624a3-126">Add the following `using` directives to the top of the code file.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="624a3-127">Aby utworzyć listę kont bankowych</span><span class="sxs-lookup"><span data-stu-id="624a3-127">To create a list of bank accounts</span></span>

1. <span data-ttu-id="624a3-128">Wklej poniższą definicję klasy do **Program.cs**w obszarze `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="624a3-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="624a3-129">Dodaj następujący kod do `Main` metodę w celu utworzenia `bankAccounts` lista, która zawiera dwa konta.</span><span class="sxs-lookup"><span data-stu-id="624a3-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="624a3-130">Do deklarowania metody, które Eksportuje informacje o koncie do programu Excel</span><span class="sxs-lookup"><span data-stu-id="624a3-130">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="624a3-131">Dodaj następującą metodę do `Program` klasy arkusza programu Excel.</span><span class="sxs-lookup"><span data-stu-id="624a3-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="624a3-132">Metoda <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> ma parametr opcjonalny służącą do konkretnego szablonu.</span><span class="sxs-lookup"><span data-stu-id="624a3-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="624a3-133">Parametry opcjonalne nowego w programie C# 4, umożliwiają pominięto argument dla tego parametru, jeśli chcesz użyć wartości domyślnej parametru.</span><span class="sxs-lookup"><span data-stu-id="624a3-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="624a3-134">Ponieważ żaden argument nie jest wysyłany w poniższym kodzie `Add` korzysta z domyślnego szablonu i utworzy nowy skoroszyt.</span><span class="sxs-lookup"><span data-stu-id="624a3-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="624a3-135">Równoważne instrukcji we wcześniejszych wersjach języka C# wymaga argumentu symbolu zastępczego: `ExcelApp.Workbooks.Add(Type.Missing)`.</span><span class="sxs-lookup"><span data-stu-id="624a3-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="624a3-136">Dodaj następujący kod na końcu `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="624a3-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="624a3-137">Kod wstawia wartości na pierwszych dwóch kolumn będących jej pierwszego wiersza arkusza.</span><span class="sxs-lookup"><span data-stu-id="624a3-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="624a3-138">Dodaj następujący kod na końcu `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="624a3-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="624a3-139">`foreach` Pętli umieszcza informacje z listy kont do kolumn pierwszych dwóch następujących po sobie wierszy arkusza.</span><span class="sxs-lookup"><span data-stu-id="624a3-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="624a3-140">Dodaj następujący kod na końcu `DisplayInExcel` można dostosowywać szerokość kolumn w celu dopasowania do zawartości.</span><span class="sxs-lookup"><span data-stu-id="624a3-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="624a3-141">Wcześniejszych wersjach języka C# wymaga jawnego rzutowania dla tych operacji, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` nadaje się program Excel <xref:Microsoft.Office.Interop.Excel.Range> metody.</span><span class="sxs-lookup"><span data-stu-id="624a3-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="624a3-142">Poniższe wiersze pokazują rzutowania.</span><span class="sxs-lookup"><span data-stu-id="624a3-142">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="624a3-143">C#4 i nowsze wersje, konwertuje zwracane `Object` do `dynamic` automatycznie, jeśli odwołuje się zestaw [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) — opcja kompilatora lub ekwiwalentnie, jeśli programu Excel **Osadź typy współdziałania** właściwość jest ustawiona na wartość true.</span><span class="sxs-lookup"><span data-stu-id="624a3-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="624a3-144">Wartość true, to wartością domyślną dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="624a3-144">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="624a3-145">Aby uruchomić projekt</span><span class="sxs-lookup"><span data-stu-id="624a3-145">To run the project</span></span>

1. <span data-ttu-id="624a3-146">Dodaj następujący wiersz na końcu `Main`.</span><span class="sxs-lookup"><span data-stu-id="624a3-146">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="624a3-147">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="624a3-147">Press CTRL+F5.</span></span>

     <span data-ttu-id="624a3-148">Arkusz programu Excel pojawi się zawierającej dane z dwóch kont.</span><span class="sxs-lookup"><span data-stu-id="624a3-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="624a3-149">Aby dodać dokument programu Word</span><span class="sxs-lookup"><span data-stu-id="624a3-149">To add a Word document</span></span>

1. <span data-ttu-id="624a3-150">Aby zilustrować dodatkowych sposobów, w którym C# 4 i nowsze wersje, rozszerza programowaniu pakietu Office, otwiera aplikację Word poniższy kod i tworzy ikony, który stanowi łącze do arkusza programu Excel.</span><span class="sxs-lookup"><span data-stu-id="624a3-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="624a3-151">Wklej metodę `CreateIconInWordDoc`, podane w dalszej części tego kroku do `Program` klasy.</span><span class="sxs-lookup"><span data-stu-id="624a3-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="624a3-152">`CreateIconInWordDoc` używa argumentów nazwanych i opcjonalnych, aby zmniejszyć złożoność wywołania metody do <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> i <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span><span class="sxs-lookup"><span data-stu-id="624a3-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="624a3-153">Te wywołania zestawowi dwóch innych nowych funkcji wprowadzonych w C# 4, które upraszczają wywołania metody COM, które mają odwołania do parametrów.</span><span class="sxs-lookup"><span data-stu-id="624a3-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="624a3-154">Po pierwsze może wysyłać argumentów do parametrów w formie odwołań, tak, jakby były one wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="624a3-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="624a3-155">Oznacza to można wysyłać wartości bezpośrednio, bez tworzenia zmienną dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="624a3-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="624a3-156">Kompilator generuje tymczasowe zmienne do przechowywania wartości argumentów i odrzuca wszystkie zmienne, po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="624a3-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="624a3-157">Po drugie, można pominąć `ref` — słowo kluczowe na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="624a3-157">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="624a3-158">`Add` Metoda ma cztery parametry odwołań, które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="624a3-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="624a3-159">W C# 4.0 i nowsze wersje, możesz pominąć argumenty poszczególnych lub wszystkich parametrów, jeśli chcesz użyć wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="624a3-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="624a3-160">W C# 3.0 i wcześniejszych wersji, należy podać argument dla każdego parametru, a argument musi być zmienną, ponieważ parametry są parametry odwołania.</span><span class="sxs-lookup"><span data-stu-id="624a3-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="624a3-161">`PasteSpecial` Metoda Wstawia zawartość Schowka.</span><span class="sxs-lookup"><span data-stu-id="624a3-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="624a3-162">Metoda ma siedem parametrów odwołania, które są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="624a3-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="624a3-163">Poniższy kod określa argumenty dwa z nich: `Link`, aby utworzyć łącze do źródła zawartości Schowka i `DisplayAsIcon`, aby wyświetlić łącza w postaci ikony.</span><span class="sxs-lookup"><span data-stu-id="624a3-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="624a3-164">W C# 4.0 i nowsze wersje, możesz użyć nazwanych argumentów dla tych dwóch i Pomiń pozostałe.</span><span class="sxs-lookup"><span data-stu-id="624a3-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="624a3-165">Mimo, że są to parametry odwołania, trzeba użyć `ref` — słowo kluczowe, lub aby utworzyć zmienne do wysyłania jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="624a3-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="624a3-166">Wartości można wysyłać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="624a3-166">You can send the values directly.</span></span> <span data-ttu-id="624a3-167">W C# 3.0 i wcześniejszych wersji, należy podać zmiennych argumentów dla każdego parametru odwołania.</span><span class="sxs-lookup"><span data-stu-id="624a3-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="624a3-168">W C# 3.0 i wcześniejszych wersji języka, że wymagane jest bardziej skomplikowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="624a3-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="624a3-169">Na koniec należy dodać następującą instrukcję `Main`.</span><span class="sxs-lookup"><span data-stu-id="624a3-169">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="624a3-170">Na koniec należy dodać następującą instrukcję `DisplayInExcel`.</span><span class="sxs-lookup"><span data-stu-id="624a3-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="624a3-171">`Copy` Metoda dodaje arkusz do Schowka.</span><span class="sxs-lookup"><span data-stu-id="624a3-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="624a3-172">Naciśnij kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="624a3-172">Press CTRL+F5.</span></span>

     <span data-ttu-id="624a3-173">Dokument programu Word wyświetlany jest wyświetlana ikona.</span><span class="sxs-lookup"><span data-stu-id="624a3-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="624a3-174">Kliknij dwukrotnie ikonę Aby przenieść arkusza na pierwszym planie.</span><span class="sxs-lookup"><span data-stu-id="624a3-174">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="624a3-175">Aby ustawić właściwość Osadź typy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="624a3-175">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="624a3-176">Dodatkowe rozszerzenia są możliwe w przypadku, gdy wywołujesz typ modelu COM, który nie wymaga podstawowego zestawu międzyoperacyjnego (PIA) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="624a3-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="624a3-177">Eliminujące zależność od wyników zestawów PIA w niezależność i łatwiejsze wdrażanie.</span><span class="sxs-lookup"><span data-stu-id="624a3-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="624a3-178">Aby uzyskać więcej informacji na temat korzyści programowanie bez zestawów PIA, zobacz [instruktażu: Osadzanie typów z zarządzanych zestawów](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="624a3-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>

     <span data-ttu-id="624a3-179">Ponadto programowania jest łatwiejsze, ponieważ typy, które są wymagane i zwracane przez metody COM mogą być reprezentowane za pomocą typu `dynamic` zamiast `Object`.</span><span class="sxs-lookup"><span data-stu-id="624a3-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="624a3-180">Zmienne, które mają typ `dynamic` nie są sprawdzane do czasu wykonywania, który eliminuje konieczność jawnego rzutowania.</span><span class="sxs-lookup"><span data-stu-id="624a3-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="624a3-181">Aby uzyskać więcej informacji, zobacz [przy użyciu typu dynamicznego](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="624a3-181">For more information, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="624a3-182">W C# 4, osadzanie typów informacji zamiast przy użyciu zestawów PIA jest zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="624a3-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="624a3-183">Z powodu tej wartości domyślnej kilka poprzednich przykładach są uproszczone, ponieważ jawne Rzutowanie nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="624a3-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="624a3-184">Na przykład deklaracja `worksheet` w `DisplayInExcel` jest zapisywany jako `Excel._Worksheet workSheet = excelApp.ActiveSheet` zamiast `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span><span class="sxs-lookup"><span data-stu-id="624a3-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="624a3-185">Wywołania `AutoFit` w tej samej metody również wymaga jawnego rzutowania bez domyślnego, ponieważ `ExcelApp.Columns[1]` zwraca `Object`, i `AutoFit` jest metodą programu Excel.</span><span class="sxs-lookup"><span data-stu-id="624a3-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="624a3-186">Poniższy kod przedstawia rzutowania.</span><span class="sxs-lookup"><span data-stu-id="624a3-186">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="624a3-187">Aby zmienić domyślny i używanie zestawów PIA, zamiast osadzanie informacji o typie, rozwiń węzeł **odwołania** w węźle **Eksploratora rozwiązań** , a następnie wybierz **Microsoft.Office.Interop.Excel** lub **Microsoft.Office.Interop.Word**.</span><span class="sxs-lookup"><span data-stu-id="624a3-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="624a3-188">Jeśli nie widzisz **właściwości** naciśnij klawisze **F4**.</span><span class="sxs-lookup"><span data-stu-id="624a3-188">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="624a3-189">Znajdź **Osadź typy współdziałania** na liście właściwości i zmień jej wartość na **False**.</span><span class="sxs-lookup"><span data-stu-id="624a3-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="624a3-190">Ekwiwalentnie można kompilować przy użyciu [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora zamiast [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="624a3-190">Equivalently, you can compile by using the [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="624a3-191">Aby dodać dodatkowe formatowanie do tabeli</span><span class="sxs-lookup"><span data-stu-id="624a3-191">To add additional formatting to the table</span></span>

1. <span data-ttu-id="624a3-192">Zastąp dwa wywołania `AutoFit` w `DisplayInExcel` przy użyciu następujących instrukcji.</span><span class="sxs-lookup"><span data-stu-id="624a3-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="624a3-193"><xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> Metoda zawiera siedem wartości parametrów, z których wszystkie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="624a3-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="624a3-194">Argumenty nazwane i opcjonalne umożliwiają argumenty dla żadnego, niektórych lub wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="624a3-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="624a3-195">W poprzednich instrukcji, argument jest dostarczany tylko dla jednego z parametrów, `Format`.</span><span class="sxs-lookup"><span data-stu-id="624a3-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="624a3-196">Ponieważ `Format` jest pierwszym parametrem na liście parametrów, nie należy podać nazwę parametru.</span><span class="sxs-lookup"><span data-stu-id="624a3-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="624a3-197">Jednak instrukcja może być łatwiejsze do zrozumienia, jeśli nazwa parametru jest uwzględniany, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="624a3-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="624a3-198">Naciśnij klawisze CTRL + F5, aby wyświetlić wynik.</span><span class="sxs-lookup"><span data-stu-id="624a3-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="624a3-199">Inne formaty są wymienione w <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="624a3-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="624a3-200">Porównaj z instrukcją w kroku 1, z użyciem następujący kod, który wyświetla argumenty, które są wymagane w C# 3.0 i wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="624a3-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="624a3-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="624a3-201">Example</span></span>

<span data-ttu-id="624a3-202">Poniższy kod przedstawia kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="624a3-202">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="624a3-203">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="624a3-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="624a3-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="624a3-204">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="624a3-205">Używanie typu dynamicznego</span><span class="sxs-lookup"><span data-stu-id="624a3-205">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="624a3-206">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="624a3-206">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="624a3-207">Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office</span><span class="sxs-lookup"><span data-stu-id="624a3-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
