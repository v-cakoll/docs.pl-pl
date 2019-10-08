---
title: 'Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu C# Office — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 90b60a6410ffbe7f9802b01bf3303b6e842a1424
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002789"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="e325a-102">Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="e325a-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>

<span data-ttu-id="e325a-103">Argumenty nazwane i opcjonalne argumenty, wprowadzone w C# 4, zwiększają wygodę, elastyczność i czytelność C# w programowaniu.</span><span class="sxs-lookup"><span data-stu-id="e325a-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="e325a-104">Ponadto te funkcje znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsy API automatyzacji Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e325a-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="e325a-105">W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnaste parametry, które reprezentują cechy tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory.</span><span class="sxs-lookup"><span data-stu-id="e325a-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="e325a-106">Wszystkie 16 parametrów są opcjonalne, ponieważ większość z nich nie chce określać konkretnych wartości dla wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="e325a-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="e325a-107">Jednakże bez argumentów nazwanych i opcjonalnych należy podać wartość lub symbol zastępczy dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="e325a-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="e325a-108">Za pomocą argumentów nazwanych i opcjonalnych można określić wartości tylko dla parametrów, które są wymagane dla projektu.</span><span class="sxs-lookup"><span data-stu-id="e325a-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="e325a-109">Aby wykonać te procedury, na komputerze musi być zainstalowany program Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="e325a-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="e325a-110">Aby utworzyć nową aplikację konsolową</span><span class="sxs-lookup"><span data-stu-id="e325a-110">To create a new console application</span></span>

1. <span data-ttu-id="e325a-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e325a-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="e325a-112">W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e325a-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="e325a-113">W okienku **Kategorie szablonów** rozwiń **element Wizualizacja C#** , a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="e325a-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="e325a-114">Poszukaj w górnej części okienka **Szablony** , aby upewnić się, że **.NET Framework 4** pojawia się w polu **platforma docelowa** .</span><span class="sxs-lookup"><span data-stu-id="e325a-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="e325a-115">W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="e325a-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="e325a-116">Wpisz nazwę projektu w polu **Nazwa** .</span><span class="sxs-lookup"><span data-stu-id="e325a-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="e325a-117">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e325a-117">Click **OK**.</span></span>

     <span data-ttu-id="e325a-118">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="e325a-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="e325a-119">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="e325a-119">To add a reference</span></span>

1. <span data-ttu-id="e325a-120">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="e325a-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="e325a-121">Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .</span><span class="sxs-lookup"><span data-stu-id="e325a-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="e325a-122">Na stronie **.NET** wybierz pozycję **Microsoft. Office. Interop. Word** na liście **Nazwa składnika** .</span><span class="sxs-lookup"><span data-stu-id="e325a-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="e325a-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="e325a-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="e325a-124">Aby dodać wymagane dyrektywy using</span><span class="sxs-lookup"><span data-stu-id="e325a-124">To add necessary using directives</span></span>

1. <span data-ttu-id="e325a-125">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *program.cs* , a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="e325a-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="e325a-126">Dodaj następujące dyrektywy `using` na początku pliku kodu:</span><span class="sxs-lookup"><span data-stu-id="e325a-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="e325a-127">Aby wyświetlić tekst w dokumencie programu Word</span><span class="sxs-lookup"><span data-stu-id="e325a-127">To display text in a Word document</span></span>

1. <span data-ttu-id="e325a-128">W klasie `Program` w *program.cs*Dodaj następującą metodę w celu utworzenia aplikacji programu Word i dokumentu programu Word.</span><span class="sxs-lookup"><span data-stu-id="e325a-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="e325a-129">Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) ma cztery parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e325a-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="e325a-130">W tym przykładzie używane są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="e325a-130">This example uses their default values.</span></span> <span data-ttu-id="e325a-131">W związku z tym nie są wymagane żadne argumenty w instrukcji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="e325a-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="e325a-132">Dodaj następujący kod na końcu metody, aby określić, gdzie ma być wyświetlany tekst w dokumencie i jaki tekst ma być wyświetlany:</span><span class="sxs-lookup"><span data-stu-id="e325a-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="e325a-133">Aby uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="e325a-133">To run the application</span></span>

1. <span data-ttu-id="e325a-134">Dodaj następującą instrukcję do głównej:</span><span class="sxs-lookup"><span data-stu-id="e325a-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="e325a-135">Naciśnij <kbd>klawisze CTRL</kbd>+<kbd>F5</kbd> , aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="e325a-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="e325a-136">Zostanie wyświetlony dokument programu Word zawierający określony tekst.</span><span class="sxs-lookup"><span data-stu-id="e325a-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="e325a-137">Aby zmienić tekst na tabelę</span><span class="sxs-lookup"><span data-stu-id="e325a-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="e325a-138">Użyj metody `ConvertToTable`, aby ująć tekst w tabeli.</span><span class="sxs-lookup"><span data-stu-id="e325a-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="e325a-139">Metoda ma szesnaste parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e325a-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="e325a-140">Funkcja IntelliSense ujmuje opcjonalne parametry w nawiasach, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="e325a-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Lista parametrów dla metody ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="e325a-142">Argumenty nazwane i opcjonalne umożliwiają określenie wartości tylko dla parametrów, które mają zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="e325a-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="e325a-143">Dodaj następujący kod na końcu metody `DisplayInWord`, aby utworzyć prostą tabelę.</span><span class="sxs-lookup"><span data-stu-id="e325a-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="e325a-144">Argument określa, że przecinki w ciągu tekstowym w `range` oddzielają komórki tabeli.</span><span class="sxs-lookup"><span data-stu-id="e325a-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="e325a-145">We wcześniejszych wersjach programu C#wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="e325a-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="e325a-146">Naciśnij <kbd>klawisze CTRL</kbd>+<kbd>F5</kbd> , aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="e325a-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="e325a-147">Aby eksperymentować z innymi parametrami</span><span class="sxs-lookup"><span data-stu-id="e325a-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="e325a-148">Aby zmienić tabelę tak, aby stała się jedną kolumną i trzema wierszami, Zastąp ostatni wiersz w `DisplayInWord` następującą instrukcją, a następnie wpisz <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e325a-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="e325a-149">Aby określić wstępnie zdefiniowany format tabeli, Zastąp ostatni wiersz w `DisplayInWord` następującą instrukcją, a następnie wpisz <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e325a-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="e325a-150">Format może być dowolną ze stałych [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) .</span><span class="sxs-lookup"><span data-stu-id="e325a-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="e325a-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="e325a-151">Example</span></span>

<span data-ttu-id="e325a-152">Poniższy kod zawiera pełny przykład:</span><span class="sxs-lookup"><span data-stu-id="e325a-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="e325a-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e325a-153">See also</span></span>

- [<span data-ttu-id="e325a-154">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="e325a-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
