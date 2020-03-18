---
title: Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714873"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="4a442-102">Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office (Przewodnik po programowaniu języka C#)</span><span class="sxs-lookup"><span data-stu-id="4a442-102">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="4a442-103">Nazwane argumenty i opcjonalne argumenty, wprowadzone w języku C# 4, zwiększają wygodę, elastyczność i czytelność w programowaniu języka C#.</span><span class="sxs-lookup"><span data-stu-id="4a442-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="4a442-104">Ponadto te funkcje znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsy API automatyzacji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="4a442-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="4a442-105">W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnaście parametrów reprezentujących cechy tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory.</span><span class="sxs-lookup"><span data-stu-id="4a442-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="4a442-106">Wszystkie szesnaście parametrów są opcjonalne, ponieważ przez większość czasu nie chcesz określać określonych wartości dla wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="4a442-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="4a442-107">Jednak bez nazwanych i opcjonalnych argumentów należy podać wartość lub wartość zastępczą dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="4a442-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="4a442-108">W przypadku argumentów nazwanych i opcjonalnych można określić wartości tylko dla parametrów, które są wymagane dla projektu.</span><span class="sxs-lookup"><span data-stu-id="4a442-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="4a442-109">Aby wykonać te procedury, na komputerze musi być zainstalowany program Microsoft Office Word.</span><span class="sxs-lookup"><span data-stu-id="4a442-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="4a442-110">Aby utworzyć nową aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="4a442-110">To create a new console application</span></span>

1. <span data-ttu-id="4a442-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a442-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="4a442-112">W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="4a442-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="4a442-113">W okienku **Kategorie szablonów** rozwiń węzeł **Visual C#,** a następnie kliknij pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="4a442-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="4a442-114">Spójrz w górnej części **okienka szablony,** aby upewnić się, że **.NET Framework 4** pojawia się w polu **Platforma docelowa.**</span><span class="sxs-lookup"><span data-stu-id="4a442-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="4a442-115">W okienku **Szablony** kliknij pozycję **Aplikacja konsoli**.</span><span class="sxs-lookup"><span data-stu-id="4a442-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="4a442-116">Wpisz nazwę projektu w polu **Nazwa.**</span><span class="sxs-lookup"><span data-stu-id="4a442-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="4a442-117">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a442-117">Click **OK**.</span></span>

     <span data-ttu-id="4a442-118">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4a442-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="4a442-119">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="4a442-119">To add a reference</span></span>

1. <span data-ttu-id="4a442-120">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="4a442-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="4a442-121">Pojawi się okno dialogowe **Dodawanie odwołania.**</span><span class="sxs-lookup"><span data-stu-id="4a442-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="4a442-122">Na stronie **.NET** wybierz pozycję **Microsoft.Office.Interop.Word** na liście **Nazwa składnika.**</span><span class="sxs-lookup"><span data-stu-id="4a442-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="4a442-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4a442-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="4a442-124">Aby dodać niezbędne za pomocą dyrektyw</span><span class="sxs-lookup"><span data-stu-id="4a442-124">To add necessary using directives</span></span>

1. <span data-ttu-id="4a442-125">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Program.cs,* a następnie kliknij polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="4a442-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="4a442-126">Dodaj następujące `using` dyrektywy do górnej części pliku kodu:</span><span class="sxs-lookup"><span data-stu-id="4a442-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="4a442-127">Aby wyświetlić tekst w dokumencie programu Word</span><span class="sxs-lookup"><span data-stu-id="4a442-127">To display text in a Word document</span></span>

1. <span data-ttu-id="4a442-128">W `Program` klasie w *Program.cs*dodaj następującą metodę tworzenia aplikacji programu Word i dokumentu programu Word.</span><span class="sxs-lookup"><span data-stu-id="4a442-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="4a442-129">[Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) Metoda ma cztery parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="4a442-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="4a442-130">W tym przykładzie użyto ich wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="4a442-130">This example uses their default values.</span></span> <span data-ttu-id="4a442-131">W związku z tym nie są konieczne żadne argumenty w instrukcji wywołującej.</span><span class="sxs-lookup"><span data-stu-id="4a442-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="4a442-132">Dodaj następujący kod na końcu metody, aby określić, gdzie ma być wyświetlany tekst w dokumencie i jaki tekst ma być wyświetlany:</span><span class="sxs-lookup"><span data-stu-id="4a442-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="4a442-133">Aby uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="4a442-133">To run the application</span></span>

1. <span data-ttu-id="4a442-134">Dodaj następującą instrukcję do Main:</span><span class="sxs-lookup"><span data-stu-id="4a442-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="4a442-135">Naciśnij <kbd>klawisz ctrl</kbd>+<kbd>f5,</kbd> aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="4a442-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="4a442-136">Zostanie wyświetlony dokument programu Word zawierający określony tekst.</span><span class="sxs-lookup"><span data-stu-id="4a442-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="4a442-137">Aby zmienić tekst na tabelę</span><span class="sxs-lookup"><span data-stu-id="4a442-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="4a442-138">Użyj `ConvertToTable` metody, aby ująć tekst w tabeli.</span><span class="sxs-lookup"><span data-stu-id="4a442-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="4a442-139">Metoda ma szesnaście parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="4a442-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="4a442-140">IntelliSense ujmuje opcjonalne parametry w nawiasy, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="4a442-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![Lista parametrów metody ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="4a442-142">Argumenty nazwane i opcjonalne umożliwiają określenie wartości tylko dla parametrów, które mają zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="4a442-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="4a442-143">Dodaj następujący kod na końcu `DisplayInWord` metody, aby utworzyć prostą tabelę.</span><span class="sxs-lookup"><span data-stu-id="4a442-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="4a442-144">Argument określa, że przecinki w `range` ciągu tekstowym w oddzielnych komórkach tabeli.</span><span class="sxs-lookup"><span data-stu-id="4a442-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="4a442-145">We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="4a442-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="4a442-146">Naciśnij <kbd>klawisz ctrl</kbd>+<kbd>f5,</kbd> aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="4a442-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="4a442-147">Aby eksperymentować z innymi parametrami</span><span class="sxs-lookup"><span data-stu-id="4a442-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="4a442-148">Aby zmienić tabelę tak, aby była ona zgodna `DisplayInWord` z jedną kolumną i trzema wierszami, należy zastąpić ostatni wiersz następującą instrukcją, a następnie <kbd>wpisz klawiszctrl</kbd>+<kbd>f5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a442-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="4a442-149">Aby określić wstępnie zdefiniowany format tabeli, zamień ostatni wiersz `DisplayInWord` na następującą instrukcję, a następnie <kbd>wpisz klawiszctrl</kbd>+<kbd>f5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4a442-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="4a442-150">Format może być dowolną ze stałych [WdTableFormat.](<xref:Microsoft.Office.Interop.Word.WdTableFormat>)</span><span class="sxs-lookup"><span data-stu-id="4a442-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="4a442-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a442-151">Example</span></span>

<span data-ttu-id="4a442-152">Poniższy kod zawiera pełny przykład:</span><span class="sxs-lookup"><span data-stu-id="4a442-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="4a442-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a442-153">See also</span></span>

- [<span data-ttu-id="4a442-154">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="4a442-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
