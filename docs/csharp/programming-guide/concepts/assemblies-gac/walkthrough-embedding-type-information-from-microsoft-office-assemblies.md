---
title: 'Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 8e7eb5c797ca87f87950d530112ec64f1327ae0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324528"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="dc730-102">Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="dc730-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="dc730-103">Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę podstawowy zestaw międzyoperacyjny (PIA).</span><span class="sxs-lookup"><span data-stu-id="dc730-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="dc730-104">Ponadto informacji osadzonym typem pozwala na osiągnięcie niezależność od wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc730-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="dc730-105">Oznacza to, że program mogą być zapisywane na używanie typów z wielu wersji biblioteki COM bez konieczności PIA określonych dla każdej wersji.</span><span class="sxs-lookup"><span data-stu-id="dc730-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="dc730-106">To jest typowym scenariuszem dla aplikacji, które korzystają z bibliotek Microsoft Office obiektów.</span><span class="sxs-lookup"><span data-stu-id="dc730-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="dc730-107">Osadzanie informacji o typie włącza tę samą kompilację programu w różnych wersjach pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="dc730-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="dc730-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="dc730-108">Prerequisites</span></span>  
 <span data-ttu-id="dc730-109">W tym przewodniku wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="dc730-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="dc730-110">Komputer, na którym zainstalowano program Microsoft Excel i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc730-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="dc730-111">Drugi komputer, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.</span><span class="sxs-lookup"><span data-stu-id="dc730-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="dc730-112">Aby utworzyć aplikację, która działa w różnych wersjach pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="dc730-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="dc730-113">Uruchom program Visual Studio na komputerze, na którym jest zainstalowany program Excel.</span><span class="sxs-lookup"><span data-stu-id="dc730-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="dc730-114">Na **pliku** menu, wybierz **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="dc730-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="dc730-115">W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="dc730-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="dc730-116">Wybierz **aplikacji konsoli** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="dc730-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="dc730-117">W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc730-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="dc730-118">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="dc730-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="dc730-119">W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania** folder, a następnie wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="dc730-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="dc730-120">Na **.NET** , wybierz pozycję najnowszą wersję `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="dc730-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="dc730-121">Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="dc730-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="dc730-122">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="dc730-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="dc730-123">Na liście odwołań dla **CreateExcelWorkbook** projektu, zaznacz odwołanie `Microsoft.Office.Interop.Excel` dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="dc730-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="dc730-124">W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.</span><span class="sxs-lookup"><span data-stu-id="dc730-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc730-125">Z powodu osadzony typ międzyoperacyjny informacji o różnych wersjach pakietu Microsoft Office jest uruchomiona aplikacja utworzone w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="dc730-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="dc730-126">Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, musi zawierać PIA dla każdej wersji pakietu Microsoft Office, aplikacja będzie uruchamiana z.</span><span class="sxs-lookup"><span data-stu-id="dc730-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="dc730-127">Otwórz **Program.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="dc730-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="dc730-128">Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="dc730-128">Replace the code in the file with the following code:</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.IO;  
    using Excel = Microsoft.Office.Interop.Excel;  
  
    namespace CreateExcelWorkbook  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                int[] values = {4, 6, 18, 2, 1, 76, 0, 3, 11};  
  
                CreateWorkbook(values, @"C:\SampleFolder\SampleWorkbook.xls");  
            }  
  
            static void CreateWorkbook(int[] values, string filePath)  
            {  
                Excel.Application excelApp = null;  
                Excel.Workbook wkbk;  
                Excel.Worksheet sheet;  
  
                try  
                {  
                        // Start Excel and create a workbook and worksheet.  
                        excelApp = new Excel.Application();  
                        wkbk = excelApp.Workbooks.Add();  
                        sheet = wkbk.Sheets.Add() as Excel.Worksheet;  
                        sheet.Name = "Sample Worksheet";  
  
                        // Write a column of values.  
                        // In the For loop, both the row index and array index start at 1.  
                        // Therefore the value of 4 at array index 0 is not included.  
                        for (int i = 1; i < values.Length; i++)  
                        {  
                            sheet.Cells[i, 1] = values[i];  
                        }  
  
                        // Suppress any alerts and save the file. Create the directory   
                        // if it does not exist. Overwrite the file if it exists.  
                        excelApp.DisplayAlerts = false;  
                        string folderPath = Path.GetDirectoryName(filePath);  
                        if (!Directory.Exists(folderPath))  
                        {  
                            Directory.CreateDirectory(folderPath);  
                        }  
                        wkbk.SaveAs(filePath);  
                }  
                catch  
                {  
                }  
                finally  
                {  
                    sheet = null;  
                    wkbk = null;  
  
                    // Close Excel.  
                    excelApp.Quit();  
                    excelApp = null;  
                }  
            }  
        }  
    }  
    ```  
  
8.  <span data-ttu-id="dc730-129">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="dc730-129">Save the project.</span></span>  
  
9. <span data-ttu-id="dc730-130">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="dc730-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="dc730-131">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="dc730-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="dc730-132">Aby opublikować aplikację na komputerze, na którym zainstalowany jest inna wersja programu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="dc730-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="dc730-133">Otwórz projekt utworzone przez tego przewodnika w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc730-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="dc730-134">Na **kompilacji** menu, wybierz **publikowania CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="dc730-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="dc730-135">Wykonaj kroki Kreatora publikowania, aby utworzyć zainstalowania wersji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc730-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="dc730-136">Aby uzyskać więcej informacji, zobacz [Kreator publikacji (Office Development w Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="dc730-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="dc730-137">Instalowanie aplikacji na komputerze, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.</span><span class="sxs-lookup"><span data-stu-id="dc730-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="dc730-138">Po zakończeniu instalacji uruchom zainstalowany program.</span><span class="sxs-lookup"><span data-stu-id="dc730-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="dc730-139">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="dc730-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc730-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc730-140">See Also</span></span>  
 [<span data-ttu-id="dc730-141">Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="dc730-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [<span data-ttu-id="dc730-142">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="dc730-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
