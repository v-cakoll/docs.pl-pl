---
title: "Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="07e79-102">Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="07e79-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>
<span data-ttu-id="07e79-103">Nazwane argumenty i argumentów opcjonalnych, wprowadzone w systemie [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zwiększenia wygody, elastyczność i możliwość odczytania w C# — programowanie.</span><span class="sxs-lookup"><span data-stu-id="07e79-103">Named arguments and optional arguments, introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="07e79-104">Ponadto te funkcje znacznie ułatwienia dostępu do interfejsów modelu COM, takich jak Microsoft Office automatyzacji interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="07e79-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>  
  
 <span data-ttu-id="07e79-105">W poniższym przykładzie metoda [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) ma parametry, które reprezentują właściwości tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania szesnastu, czcionki i kolory.</span><span class="sxs-lookup"><span data-stu-id="07e79-105">In the following example, method [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="07e79-106">Wszystkie szesnastu parametry są opcjonalne, ponieważ w większości przypadków nie chcesz określać wartości określonej dla wszystkich z nich.</span><span class="sxs-lookup"><span data-stu-id="07e79-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="07e79-107">Jednak bez argumenty nazwane i opcjonalne, wartość lub wartość symbolu zastępczego musi zostać podany dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="07e79-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="07e79-108">Z argumenty nazwane i opcjonalne możesz określić wartości tylko dla parametrów, które są wymagane dla projektu.</span><span class="sxs-lookup"><span data-stu-id="07e79-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>  
  
 <span data-ttu-id="07e79-109">Musi mieć program Microsoft Office Word zainstalowany na tym komputerze do wykonania tych procedur.</span><span class="sxs-lookup"><span data-stu-id="07e79-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="07e79-110">Aby utworzyć nową aplikację konsoli</span><span class="sxs-lookup"><span data-stu-id="07e79-110">To create a new console application</span></span>  
  
1.  <span data-ttu-id="07e79-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07e79-111">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="07e79-112">Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="07e79-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="07e79-113">W **kategorii Szablony** okienku rozwiń **Visual C#**, a następnie kliknij przycisk **Windows**.</span><span class="sxs-lookup"><span data-stu-id="07e79-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="07e79-114">Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4** pojawia się w **platformy docelowej** pole.</span><span class="sxs-lookup"><span data-stu-id="07e79-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>  
  
5.  <span data-ttu-id="07e79-115">W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="07e79-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="07e79-116">Wpisz nazwę projektu w **nazwa** pola.</span><span class="sxs-lookup"><span data-stu-id="07e79-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="07e79-117">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="07e79-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="07e79-118">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="07e79-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-a-reference"></a><span data-ttu-id="07e79-119">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="07e79-119">To add a reference</span></span>  
  
1.  <span data-ttu-id="07e79-120">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="07e79-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="07e79-121">**Dodaj odwołanie** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="07e79-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="07e79-122">Na **.NET** wybierz pozycję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy.</span><span class="sxs-lookup"><span data-stu-id="07e79-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>  
  
3.  <span data-ttu-id="07e79-123">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="07e79-123">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="07e79-124">Aby dodać niezbędne przy użyciu dyrektyw</span><span class="sxs-lookup"><span data-stu-id="07e79-124">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="07e79-125">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="07e79-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="07e79-126">Dodaj następujące `using` dyrektywy na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="07e79-126">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="07e79-127">Do wyświetlania tekstu w dokumencie programu Word</span><span class="sxs-lookup"><span data-stu-id="07e79-127">To display text in a Word document</span></span>  
  
1.  <span data-ttu-id="07e79-128">W `Program` klasy w pliku Program.cs, dodaj następującą metodę do tworzenia aplikacji programu Word i dokument programu Word.</span><span class="sxs-lookup"><span data-stu-id="07e79-128">In the `Program` class in Program.cs, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="07e79-129">[Dodaj](http://go.microsoft.com/fwlink/?LinkId=145381) metoda ma cztery następujące parametry opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="07e79-129">The [Add](http://go.microsoft.com/fwlink/?LinkId=145381) method has four optional parameters.</span></span> <span data-ttu-id="07e79-130">W tym przykładzie używane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="07e79-130">This example uses their default values.</span></span> <span data-ttu-id="07e79-131">W związku z tym bez argumentów są niezbędne w instrukcji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="07e79-131">Therefore, no arguments are necessary in the calling statement.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  <span data-ttu-id="07e79-132">Dodaj następujący kod na końcu metody, aby określić, gdzie do wyświetlania tekstu w dokumencie i tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="07e79-132">Add the following code at the end of the method to define where to display text in the document, and what text to display.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a><span data-ttu-id="07e79-133">Aby uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="07e79-133">To run the application</span></span>  
  
1.  <span data-ttu-id="07e79-134">Dodaj następującą instrukcję do widoku głównego.</span><span class="sxs-lookup"><span data-stu-id="07e79-134">Add the following statement to Main.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  <span data-ttu-id="07e79-135">Naciśnij klawisze CTRL + F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="07e79-135">Press CTRL+F5 to run the project.</span></span> <span data-ttu-id="07e79-136">Pojawia się dokument programu Word, który zawiera określony tekst.</span><span class="sxs-lookup"><span data-stu-id="07e79-136">A Word document appears that contains the specified text.</span></span>  
  
### <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="07e79-137">Aby zmienić tekst do tabeli</span><span class="sxs-lookup"><span data-stu-id="07e79-137">To change the text to a table</span></span>  
  
1.  <span data-ttu-id="07e79-138">Użyj `ConvertToTable` metodę, aby umieścić tekst w tabeli.</span><span class="sxs-lookup"><span data-stu-id="07e79-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="07e79-139">Metoda ma następujące parametry opcjonalne szesnastu.</span><span class="sxs-lookup"><span data-stu-id="07e79-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="07e79-140">IntelliSense obejmuje następujące parametry opcjonalne w nawiasach, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="07e79-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="07e79-141">![Lista parametrów dla metody ConvertToTable. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span><span class="sxs-lookup"><span data-stu-id="07e79-141">![List of parameters for ConvertToTable method.](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")</span></span>  
<span data-ttu-id="07e79-142">Parametry ConvertToTable</span><span class="sxs-lookup"><span data-stu-id="07e79-142">ConvertToTable parameters</span></span>  
  
     <span data-ttu-id="07e79-143">Nazwane i opcjonalne argumenty umożliwiają określenie wartości parametrów, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="07e79-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="07e79-144">Dodaj następujący kod na końcu metody `DisplayInWord` utworzyć prostą tabelę.</span><span class="sxs-lookup"><span data-stu-id="07e79-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="07e79-145">Argument określa, że przecinkami w tekście ciąg w `range` oddzielnych komórek tabeli.</span><span class="sxs-lookup"><span data-stu-id="07e79-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     <span data-ttu-id="07e79-146">We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07e79-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  <span data-ttu-id="07e79-147">Naciśnij klawisze CTRL + F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="07e79-147">Press CTRL+F5 to run the project.</span></span>  
  
### <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="07e79-148">Aby wypróbować inne parametry</span><span class="sxs-lookup"><span data-stu-id="07e79-148">To experiment with other parameters</span></span>  
  
1.  <span data-ttu-id="07e79-149">Aby zmienić tabeli, dzięki czemu zawiera jedną kolumnę i trzy wiersze, należy zastąpić w ostatnim wierszu `DisplayInWord` z poniższych instrukcji, a następnie wpisz CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="07e79-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  <span data-ttu-id="07e79-150">Aby określić format wstępnie zdefiniowane dla tabeli, należy zastąpić w ostatnim wierszu `DisplayInWord` z poniższych instrukcji, a następnie wpisz CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="07e79-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type CTRL+F5.</span></span> <span data-ttu-id="07e79-151">Format może być dowolny z [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) stałe.</span><span class="sxs-lookup"><span data-stu-id="07e79-151">The format can be any of the [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) constants.</span></span>  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a><span data-ttu-id="07e79-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="07e79-152">Example</span></span>  
 <span data-ttu-id="07e79-153">Poniższy kod obejmuje pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="07e79-153">The following code includes the full example.</span></span>  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="07e79-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07e79-154">See Also</span></span>  
 [<span data-ttu-id="07e79-155">Argumenty nazwane i opcjonalne</span><span class="sxs-lookup"><span data-stu-id="07e79-155">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
