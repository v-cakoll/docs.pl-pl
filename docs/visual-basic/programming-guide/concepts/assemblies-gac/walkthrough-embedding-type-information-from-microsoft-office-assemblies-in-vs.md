---
title: 'Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: bc8f7585964bdd60bac5d5a466f6276fab288c78
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45668213"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="b95da-102">Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b95da-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="b95da-103">Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę zestawu podstawowej usługi międzyoperacyjnej (PIA).</span><span class="sxs-lookup"><span data-stu-id="b95da-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="b95da-104">Ponadto informacje o typie osadzony umożliwia osiągnąć niezależność Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b95da-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="b95da-105">Oznacza to by używał typów z wielu wersji biblioteki COM bez konieczności określonego PIA dla każdej wersji można napisać program.</span><span class="sxs-lookup"><span data-stu-id="b95da-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="b95da-106">Jest to typowy scenariusz w przypadku aplikacji korzystających z bibliotek Microsoft Office obiektów.</span><span class="sxs-lookup"><span data-stu-id="b95da-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="b95da-107">Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="b95da-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="b95da-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="b95da-108">Prerequisites</span></span>  
 <span data-ttu-id="b95da-109">Ten przewodnik wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="b95da-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="b95da-110">Komputer, na którym zainstalowano program Visual Studio i programu Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="b95da-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="b95da-111">Drugi komputer, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.</span><span class="sxs-lookup"><span data-stu-id="b95da-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="b95da-112">Aby utworzyć aplikację, która działa z wieloma wersjami pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="b95da-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="b95da-113">Uruchom program Visual Studio na komputerze, na którym zainstalowany jest program Excel.</span><span class="sxs-lookup"><span data-stu-id="b95da-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="b95da-114">Na **pliku** menu, wybierz **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="b95da-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="b95da-115">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="b95da-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="b95da-116">Wybierz **aplikację Konsolową** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="b95da-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="b95da-117">W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b95da-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="b95da-118">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="b95da-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="b95da-119">Otwórz menu skrótów projektu CreateExcelWorkbook, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b95da-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="b95da-120">Wybierz **odwołania** kartę. Wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b95da-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="b95da-121">Na **.NET** karty, wybierz najnowszą wersję `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="b95da-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="b95da-122">Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="b95da-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="b95da-123">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b95da-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="b95da-124">Na liście odwołań dla **CreateExcelWorkbook** projektu, wybierz odwołanie do `Microsoft.Office.Interop.Excel` dodanej w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="b95da-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="b95da-125">W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.</span><span class="sxs-lookup"><span data-stu-id="b95da-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b95da-126">Aplikacja utworzona w tym instruktażu działa z różnymi wersjami pakietu Microsoft Office z powodu informacji osadzonego typu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b95da-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="b95da-127">Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, należy uwzględnić PIA dla każdej wersji pakietu Microsoft Office, aplikacja zostanie uruchomiona przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="b95da-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="b95da-128">Otwórz plik Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="b95da-128">Open the Module1.vb file.</span></span> <span data-ttu-id="b95da-129">Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="b95da-129">Replace the code in the file with the following code:</span></span>  
  
    ```vb  
    Imports Excel = Microsoft.Office.Interop.Excel  
  
    Module Module1  
  
        Sub Main()  
            Dim values = {4, 6, 18, 2, 1, 76, 0, 3, 11}  
  
            CreateWorkbook(values, "C:\SampleFolder\SampleWorkbook.xls")  
        End Sub  
  
        Sub CreateWorkbook(ByVal values As Integer(), ByVal filePath As String)  
            Dim excelApp As Excel.Application = Nothing  
            Dim wkbk As Excel.Workbook  
            Dim sheet As Excel.Worksheet  
  
            Try  
                ' Start Excel and create a workbook and worksheet.  
                excelApp = New Excel.Application  
                wkbk = excelApp.Workbooks.Add()  
                sheet = CType(wkbk.Sheets.Add(), Excel.Worksheet)  
                sheet.Name = "Sample Worksheet"  
  
                ' Write a column of values.  
                ' In the For loop, both the row index and array index start at 1.  
                ' Therefore the value of 4 at array index 0 is not included.  
                For i = 1 To values.Length - 1  
                    sheet.Cells(i, 1) = values(i)  
                Next  
  
                ' Suppress any alerts and save the file. Create the directory   
                ' if it does not exist. Overwrite the file if it exists.  
                excelApp.DisplayAlerts = False  
                Dim folderPath = My.Computer.FileSystem.GetParentPath(filePath)  
                If Not My.Computer.FileSystem.DirectoryExists(folderPath) Then  
                    My.Computer.FileSystem.CreateDirectory(folderPath)  
                End If  
                wkbk.SaveAs(filePath)  
        Catch  
  
            Finally  
                sheet = Nothing  
                wkbk = Nothing  
  
                ' Close Excel.  
                excelApp.Quit()  
                excelApp = Nothing  
            End Try  
  
        End Sub  
    End Module  
    ```  
  
8.  <span data-ttu-id="b95da-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="b95da-130">Save the project.</span></span>  
  
9. <span data-ttu-id="b95da-131">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="b95da-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="b95da-132">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="b95da-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="b95da-133">Aby opublikować aplikację na komputerze, na którym zainstalowano inną wersję programu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="b95da-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="b95da-134">Otwórz projekt utworzony w tym instruktażu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b95da-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b95da-135">Na **kompilacji** menu, wybierz **Publikuj CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="b95da-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="b95da-136">Wykonaj kroki Kreatora publikacji, aby utworzyć instalowalną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b95da-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="b95da-137">Aby uzyskać więcej informacji, zobacz [Kreatora publikacji (Office Development w programie Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b95da-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).</span></span>  
  
3.  <span data-ttu-id="b95da-138">Zainstaluj aplikację na komputerze, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.</span><span class="sxs-lookup"><span data-stu-id="b95da-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="b95da-139">Po zakończeniu instalacji uruchom zainstalowany program.</span><span class="sxs-lookup"><span data-stu-id="b95da-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="b95da-140">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="b95da-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95da-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b95da-141">See also</span></span>

- [<span data-ttu-id="b95da-142">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b95da-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
- [<span data-ttu-id="b95da-143">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b95da-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
