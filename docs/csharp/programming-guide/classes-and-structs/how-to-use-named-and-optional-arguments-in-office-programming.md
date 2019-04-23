---
title: 'Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 3ecea9d55ef61d2158da0dabeca22a58460b3bea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313973"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="95aa0-102">Instrukcje: Użycie argumentów nazwanych i opcjonalnych w programowaniu Office (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="95aa0-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="95aa0-103">Nazwy argumentów i argumenty opcjonalne, wprowadzona w [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zwiększenia wygody, elastyczność i czytelności w programowaniu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="95aa0-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="95aa0-104">Ponadto funkcje te znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsów API automatyzacji programu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="95aa0-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="95aa0-105">W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnastu parametrów, które reprezentują cech tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory.</span><span class="sxs-lookup"><span data-stu-id="95aa0-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="95aa0-106">Wszystkie parametry szesnastu są opcjonalne, ponieważ w większości przypadków nie chcesz określać wartości określonej dla wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="95aa0-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="95aa0-107">Jednak bez argumenty nazwane i opcjonalne, wartość lub wartość symbolu zastępczego musi zostać dostarczona dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="95aa0-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="95aa0-108">Argumenty nazwane i opcjonalne należy określić tylko wartości parametrów, które są wymagane dla projektu.</span><span class="sxs-lookup"><span data-stu-id="95aa0-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="95aa0-109">Konieczne jest posiadanie programu Microsoft Office Word zainstalowany na tym komputerze do wykonania tych procedur.</span><span class="sxs-lookup"><span data-stu-id="95aa0-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="95aa0-110">Aby utworzyć nową aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="95aa0-110">To create a new console application</span></span>  
  
1. <span data-ttu-id="95aa0-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95aa0-111">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="95aa0-112">Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3. <span data-ttu-id="95aa0-113">W **kategorie szablonów** okienku rozwiń **Visual C#**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4. <span data-ttu-id="95aa0-114">Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4** pojawia się w **platformę docelową** pole.</span><span class="sxs-lookup"><span data-stu-id="95aa0-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5. <span data-ttu-id="95aa0-115">W **szablony** okienku kliknij **aplikację Konsolową**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6. <span data-ttu-id="95aa0-116">Wpisz nazwę dla projektu w **nazwa** pola.</span><span class="sxs-lookup"><span data-stu-id="95aa0-116">Type a name for your project in the **Name** field.</span></span>  
  
7. <span data-ttu-id="95aa0-117">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="95aa0-118">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="95aa0-119">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="95aa0-119">To add a reference</span></span>  
  
1. <span data-ttu-id="95aa0-120">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="95aa0-121">**Dodaj odwołanie** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="95aa0-121">The **Add Reference** dialog box appears.</span></span>  
  
2. <span data-ttu-id="95aa0-122">Na **.NET** wybierz opcję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy.</span><span class="sxs-lookup"><span data-stu-id="95aa0-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3. <span data-ttu-id="95aa0-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="95aa0-124">Aby dodać niezbędne dyrektyw using</span><span class="sxs-lookup"><span data-stu-id="95aa0-124">To add necessary using directives</span></span>  
  
1. <span data-ttu-id="95aa0-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="95aa0-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="95aa0-126">Dodaj następujący kod `using` dyrektywy na górze pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="95aa0-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="95aa0-127">Do wyświetlania tekstu w dokumencie programu Word</span><span class="sxs-lookup"><span data-stu-id="95aa0-127">To display text in a Word document</span></span>  
  
1. <span data-ttu-id="95aa0-128">W `Program` klasy w pliku Program.cs, dodaj następującą metodę do tworzenia aplikacji programu Word i dokument programu Word.</span><span class="sxs-lookup"><span data-stu-id="95aa0-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="95aa0-129">[Dodaj](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) metoda ma cztery następujące parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="95aa0-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="95aa0-130">W tym przykładzie użyto wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="95aa0-130">This example uses their default values.</span></span> <span data-ttu-id="95aa0-131">W związku z tym bez argumentów są niezbędne w instrukcji wywołujące.</span><span class="sxs-lookup"><span data-stu-id="95aa0-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]  
  
2. <span data-ttu-id="95aa0-132">Dodaj następujący kod na końcu metody do definiowania miejsca do wyświetlania tekstu w dokumencie i jakie tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="95aa0-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="95aa0-133">Aby uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="95aa0-133">To run the application</span></span>  
  
1. <span data-ttu-id="95aa0-134">Dodaj następującą instrukcję dla metody Main.</span><span class="sxs-lookup"><span data-stu-id="95aa0-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]  
  
2. <span data-ttu-id="95aa0-135">Naciśnij klawisze CTRL + F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="95aa0-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="95aa0-136">Dokument programu Word pojawia się, który zawiera określony tekst.</span><span class="sxs-lookup"><span data-stu-id="95aa0-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="95aa0-137">Aby zmienić tekst na tabelę</span><span class="sxs-lookup"><span data-stu-id="95aa0-137">To change the text to a table</span></span>  
  
1. <span data-ttu-id="95aa0-138">Użyj `ConvertToTable` metodę, aby umieścić tekst w tabeli.</span><span class="sxs-lookup"><span data-stu-id="95aa0-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="95aa0-139">Metoda ma szesnastu parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="95aa0-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="95aa0-140">Funkcja IntelliSense zawiera następujące parametry opcjonalne w nawiasach kwadratowych, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="95aa0-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     ![Lista parametrów dla metody ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)  
  
     <span data-ttu-id="95aa0-142">Nazwane i opcjonalne argumenty umożliwiają określenie wartości parametrów, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="95aa0-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="95aa0-143">Dodaj następujący kod na końcu metody `DisplayInWord` do utworzenia prostej tabeli.</span><span class="sxs-lookup"><span data-stu-id="95aa0-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="95aa0-144">Argument określa, że przecinkami w tekście ciągu w `range` oddziel komórki tabeli.</span><span class="sxs-lookup"><span data-stu-id="95aa0-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]  
  
     <span data-ttu-id="95aa0-145">We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="95aa0-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]  
  
2. <span data-ttu-id="95aa0-146">Naciśnij klawisze CTRL + F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="95aa0-146">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="95aa0-147">Aby eksperymentować z innych parametrów</span><span class="sxs-lookup"><span data-stu-id="95aa0-147">To experiment with other parameters</span></span>  
  
1. <span data-ttu-id="95aa0-148">Zmiany w tabeli, aby jedna kolumna i trzema wierszami, Zamień w ostatnim wierszu `DisplayInWord` z następującą instrukcję, a następnie wpisz kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="95aa0-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]  
  
2. <span data-ttu-id="95aa0-149">Aby określić wstępnie zdefiniowany format dla tabeli, należy zastąpić w ostatnim wierszu `DisplayInWord` z następującą instrukcję, a następnie wpisz kombinację klawiszy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="95aa0-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="95aa0-150">Format może być dowolny z [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) stałe.</span><span class="sxs-lookup"><span data-stu-id="95aa0-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]  
  
## <a name="example"></a><span data-ttu-id="95aa0-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="95aa0-151">Example</span></span>  
 <span data-ttu-id="95aa0-152">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="95aa0-152">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="95aa0-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95aa0-153">See also</span></span>

- [<span data-ttu-id="95aa0-154">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="95aa0-154">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
