---
title: "Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26e6fee5147e8477c64f7eaf0dc2aeb928c13e15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="3a995-102">Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a995-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="3a995-103">Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę podstawowy zestaw międzyoperacyjny (PIA).</span><span class="sxs-lookup"><span data-stu-id="3a995-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="3a995-104">Ponadto informacji osadzonym typem pozwala na osiągnięcie niezależność od wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a995-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="3a995-105">Oznacza to, że program mogą być zapisywane na używanie typów z wielu wersji biblioteki COM bez konieczności PIA określonych dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="3a995-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="3a995-106">To jest typowym scenariuszem dla aplikacji, które korzystają z bibliotek Microsoft Office obiektów.</span><span class="sxs-lookup"><span data-stu-id="3a995-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="3a995-107">Osadzanie informacji o typie włącza tę samą kompilację programu w różnych wersjach pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="3a995-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="3a995-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="3a995-108">Prerequisites</span></span>  
 <span data-ttu-id="3a995-109">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="3a995-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="3a995-110">Komputer, na którym zainstalowano program Microsoft Excel i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a995-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="3a995-111">Drugi komputer, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.</span><span class="sxs-lookup"><span data-stu-id="3a995-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a><span data-ttu-id="3a995-112">Aby utworzyć aplikację, która działa w różnych wersjach pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="3a995-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="3a995-113">Uruchom program Visual Studio na komputerze, na którym jest zainstalowany program Excel.</span><span class="sxs-lookup"><span data-stu-id="3a995-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="3a995-114">Na **pliku** menu, wybierz **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3a995-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="3a995-115">W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="3a995-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="3a995-116">Wybierz **aplikacji konsoli** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="3a995-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="3a995-117">W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3a995-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="3a995-118">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="3a995-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="3a995-119">Otwórz menu skrótów projektu CreateExcelWorkbook, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3a995-119">Open the shortcut menu for the CreateExcelWorkbook project and then choose **Properties**.</span></span> <span data-ttu-id="3a995-120">Wybierz **odwołania** kartę. Wybierz **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3a995-120">Choose the **References** tab. Choose the **Add** button.</span></span>  
  
5.  <span data-ttu-id="3a995-121">Na **.NET** , wybierz pozycję najnowszą wersję `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="3a995-121">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="3a995-122">Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="3a995-122">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="3a995-123">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3a995-123">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="3a995-124">Na liście odwołań dla **CreateExcelWorkbook** projektu, zaznacz odwołanie `Microsoft.Office.Interop.Excel` dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="3a995-124">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="3a995-125">W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.</span><span class="sxs-lookup"><span data-stu-id="3a995-125">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3a995-126">Z powodu osadzony typ międzyoperacyjny informacji o różnych wersjach pakietu Microsoft Office jest uruchomiona aplikacja utworzone w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="3a995-126">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="3a995-127">Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, musi zawierać PIA dla każdej wersji pakietu Microsoft Office, aplikacja będzie uruchamiana z.</span><span class="sxs-lookup"><span data-stu-id="3a995-127">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="3a995-128">Otwórz plik Module1.vb.</span><span class="sxs-lookup"><span data-stu-id="3a995-128">Open the Module1.vb file.</span></span> <span data-ttu-id="3a995-129">Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="3a995-129">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="3a995-130">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="3a995-130">Save the project.</span></span>  
  
9. <span data-ttu-id="3a995-131">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="3a995-131">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="3a995-132">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="3a995-132">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a><span data-ttu-id="3a995-133">Aby opublikować aplikację na komputerze, na którym zainstalowany jest inna wersja programu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="3a995-133">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="3a995-134">Otwórz projekt utworzone przez tego przewodnika w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3a995-134">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3a995-135">Na **kompilacji** menu, wybierz **publikowania CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="3a995-135">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="3a995-136">Wykonaj kroki Kreatora publikowania, aby utworzyć zainstalowania wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a995-136">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="3a995-137">Aby uzyskać więcej informacji, zobacz [Kreator publikacji (Office Development w Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="3a995-137">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="3a995-138">Instalowanie aplikacji na komputerze, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.</span><span class="sxs-lookup"><span data-stu-id="3a995-138">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="3a995-139">Po zakończeniu instalacji uruchom zainstalowany program.</span><span class="sxs-lookup"><span data-stu-id="3a995-139">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="3a995-140">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="3a995-140">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a995-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a995-141">See Also</span></span>  
 [<span data-ttu-id="3a995-142">Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a995-142">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="3a995-143">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a995-143">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
