---
title: 'Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: e4958c56add4f6302af3c7766b90fa4dbd58ec86
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43671150"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a><span data-ttu-id="48a8b-102">Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="48a8b-102">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>
<span data-ttu-id="48a8b-103">Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę zestawu podstawowej usługi międzyoperacyjnej (PIA).</span><span class="sxs-lookup"><span data-stu-id="48a8b-103">If you embed type information in an application that references COM objects, you can eliminate the need for a primary interop assembly (PIA).</span></span> <span data-ttu-id="48a8b-104">Ponadto informacje o typie osadzony umożliwia osiągnąć niezależność Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48a8b-104">Additionally, the embedded type information enables you to achieve version independence for your application.</span></span> <span data-ttu-id="48a8b-105">Oznacza to by używał typów z wielu wersji biblioteki COM bez konieczności określonego PIA dla każdej wersji można napisać program.</span><span class="sxs-lookup"><span data-stu-id="48a8b-105">That is, your program can be written to use types from multiple versions of a COM library without requiring a specific PIA for each version.</span></span> <span data-ttu-id="48a8b-106">Jest to typowy scenariusz w przypadku aplikacji korzystających z bibliotek Microsoft Office obiektów.</span><span class="sxs-lookup"><span data-stu-id="48a8b-106">This is a common scenario for applications that use objects from Microsoft Office libraries.</span></span> <span data-ttu-id="48a8b-107">Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="48a8b-107">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers without the need to redeploy either the program or the PIA for each version of Microsoft Office.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a><span data-ttu-id="48a8b-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="48a8b-108">Prerequisites</span></span>  
 <span data-ttu-id="48a8b-109">Ten przewodnik wymaga następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="48a8b-109">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="48a8b-110">Komputer, na którym zainstalowano program Visual Studio i programu Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="48a8b-110">A computer on which Visual Studio and Microsoft Excel are installed.</span></span>  
  
-   <span data-ttu-id="48a8b-111">Drugi komputer, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.</span><span class="sxs-lookup"><span data-stu-id="48a8b-111">A second computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
##  <a name="BKMK_createapp"></a> <span data-ttu-id="48a8b-112">Aby utworzyć aplikację, która działa z wieloma wersjami pakietu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="48a8b-112">To create an application that works with multiple versions of Microsoft Office</span></span>  
  
1.  <span data-ttu-id="48a8b-113">Uruchom program Visual Studio na komputerze, na którym zainstalowany jest program Excel.</span><span class="sxs-lookup"><span data-stu-id="48a8b-113">Start Visual Studio on a computer on which Excel is installed.</span></span>  
  
2.  <span data-ttu-id="48a8b-114">Na **pliku** menu, wybierz **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="48a8b-114">On the **File** menu, choose **New**, **Project**.</span></span>  
  
3.  <span data-ttu-id="48a8b-115">W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="48a8b-115">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="48a8b-116">Wybierz **aplikację Konsolową** w **szablony** okienka.</span><span class="sxs-lookup"><span data-stu-id="48a8b-116">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="48a8b-117">W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="48a8b-117">In the **Name** box, enter `CreateExcelWorkbook`, and then choose the **OK** button.</span></span> <span data-ttu-id="48a8b-118">Nowy projekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="48a8b-118">The new project is created.</span></span>  
  
4.  <span data-ttu-id="48a8b-119">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **odwołania** folder, a następnie wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="48a8b-119">In **Solution Explorer**, open the shortcut menu for the **References** folder and then choose **Add Reference**.</span></span>  
  
5.  <span data-ttu-id="48a8b-120">Na **.NET** karty, wybierz najnowszą wersję `Microsoft.Office.Interop.Excel`.</span><span class="sxs-lookup"><span data-stu-id="48a8b-120">On the **.NET** tab, choose the most recent version of `Microsoft.Office.Interop.Excel`.</span></span> <span data-ttu-id="48a8b-121">Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="48a8b-121">For example, **Microsoft.Office.Interop.Excel 14.0.0.0**.</span></span> <span data-ttu-id="48a8b-122">Wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="48a8b-122">Choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="48a8b-123">Na liście odwołań dla **CreateExcelWorkbook** projektu, wybierz odwołanie do `Microsoft.Office.Interop.Excel` dodanej w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="48a8b-123">In the list of references for the **CreateExcelWorkbook** project, select the reference for `Microsoft.Office.Interop.Excel` that you added in the previous step.</span></span> <span data-ttu-id="48a8b-124">W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.</span><span class="sxs-lookup"><span data-stu-id="48a8b-124">In the **Properties** window, make sure that the `Embed Interop Types` property is set to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48a8b-125">Aplikacja utworzona w tym instruktażu działa z różnymi wersjami pakietu Microsoft Office z powodu informacji osadzonego typu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="48a8b-125">The application created in this walkthrough runs with different versions of Microsoft Office because of the embedded interop type information.</span></span> <span data-ttu-id="48a8b-126">Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, należy uwzględnić PIA dla każdej wersji pakietu Microsoft Office, aplikacja zostanie uruchomiona przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="48a8b-126">If the `Embed Interop Types` property is set to `False`, you must include a PIA for each version of Microsoft Office that the application will run with.</span></span>  
  
7.  <span data-ttu-id="48a8b-127">Otwórz **Program.cs** pliku.</span><span class="sxs-lookup"><span data-stu-id="48a8b-127">Open the **Program.cs** file.</span></span> <span data-ttu-id="48a8b-128">Zastąp kod w pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="48a8b-128">Replace the code in the file with the following code:</span></span>  
  
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
  
8.  <span data-ttu-id="48a8b-129">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="48a8b-129">Save the project.</span></span>  
  
9. <span data-ttu-id="48a8b-130">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="48a8b-130">Press CTRL+F5 to build and run the project.</span></span> <span data-ttu-id="48a8b-131">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="48a8b-131">Verify that an Excel workbook has been created at the location specified in the example code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
##  <a name="BKMK_publishapp"></a> <span data-ttu-id="48a8b-132">Aby opublikować aplikację na komputerze, na którym zainstalowano inną wersję programu Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="48a8b-132">To publish the application to a computer on which a different version of Microsoft Office is installed</span></span>  
  
1.  <span data-ttu-id="48a8b-133">Otwórz projekt utworzony w tym instruktażu w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="48a8b-133">Open the project created by this walkthrough in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="48a8b-134">Na **kompilacji** menu, wybierz **Publikuj CreateExcelWorkbook**.</span><span class="sxs-lookup"><span data-stu-id="48a8b-134">On the **Build** menu, choose **Publish CreateExcelWorkbook**.</span></span> <span data-ttu-id="48a8b-135">Wykonaj kroki Kreatora publikacji, aby utworzyć instalowalną wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48a8b-135">Follow the steps of the Publish Wizard to create an installable version of the application.</span></span> <span data-ttu-id="48a8b-136">Aby uzyskać więcej informacji, zobacz [Kreatora publikacji (Office Development w programie Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span><span class="sxs-lookup"><span data-stu-id="48a8b-136">For more information, see [Publish Wizard (Office Development in Visual Studio)](https://msdn.microsoft.com/library/bb625071).</span></span>  
  
3.  <span data-ttu-id="48a8b-137">Zainstaluj aplikację na komputerze, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.</span><span class="sxs-lookup"><span data-stu-id="48a8b-137">Install the application on a computer on which the .NET Framework 4 or higher and a different version of Excel are installed.</span></span>  
  
4.  <span data-ttu-id="48a8b-138">Po zakończeniu instalacji uruchom zainstalowany program.</span><span class="sxs-lookup"><span data-stu-id="48a8b-138">When the installation is finished, run the installed program.</span></span>  
  
5.  <span data-ttu-id="48a8b-139">Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.</span><span class="sxs-lookup"><span data-stu-id="48a8b-139">Verify that an Excel workbook has been created at the location specified in the sample code: C:\SampleFolder\SampleWorkbook.xls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a8b-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48a8b-140">See Also</span></span>

- [<span data-ttu-id="48a8b-141">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="48a8b-141">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [<span data-ttu-id="48a8b-142">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="48a8b-142">/link (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
