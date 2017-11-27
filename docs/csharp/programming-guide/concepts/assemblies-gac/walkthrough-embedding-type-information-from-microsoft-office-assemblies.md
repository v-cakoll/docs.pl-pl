---
title: "Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 45ec4521da08a9a1f4bdc3b433d3f8d765960526
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (C#)
Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę podstawowy zestaw międzyoperacyjny (PIA). Ponadto informacji osadzonym typem pozwala na osiągnięcie niezależność od wersji aplikacji. Oznacza to, że program mogą być zapisywane na używanie typów z wielu wersji biblioteki COM bez konieczności PIA określonych dla każdej wersji. To jest typowym scenariuszem dla aplikacji, które korzystają z bibliotek Microsoft Office obiektów. Osadzanie informacji o typie włącza tę samą kompilację programu w różnych wersjach pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym przewodniku wymaga następujących elementów:  
  
-   Komputer, na którym zainstalowano program Microsoft Excel i Visual Studio.  
  
-   Drugi komputer, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.  
  
##  <a name="BKMK_createapp"></a>Aby utworzyć aplikację, która działa w różnych wersjach pakietu Microsoft Office  
  
1.  Uruchom program Visual Studio na komputerze, na którym jest zainstalowany program Excel.  
  
2.  Na **pliku** menu, wybierz **nowy**, **projektu**.  
  
3.  W **nowy projekt** okna dialogowego, **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikacji konsoli** w **szablony** okienka. W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz pozycję **OK** przycisku. Nowy projekt zostanie utworzony.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **odwołania** folder, a następnie wybierz **Dodaj odwołanie**.  
  
5.  Na **.NET** , wybierz pozycję najnowszą wersję `Microsoft.Office.Interop.Excel`. Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**. Wybierz **OK** przycisku.  
  
6.  Na liście odwołań dla **CreateExcelWorkbook** projektu, zaznacz odwołanie `Microsoft.Office.Interop.Excel` dodanym w poprzednim kroku. W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.  
  
    > [!NOTE]
    >  Z powodu osadzony typ międzyoperacyjny informacji o różnych wersjach pakietu Microsoft Office jest uruchomiona aplikacja utworzone w tym przewodniku. Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, musi zawierać PIA dla każdej wersji pakietu Microsoft Office, aplikacja będzie uruchamiana z.  
  
7.  Otwórz **Program.cs** pliku. Zastąp kod w pliku następującym kodem:  
  
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
  
8.  Zapisz projekt.  
  
9. Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt. Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a>Aby opublikować aplikację na komputerze, na którym zainstalowany jest inna wersja programu Microsoft Office  
  
1.  Otwórz projekt utworzone przez tego przewodnika w programie Visual Studio.  
  
2.  Na **kompilacji** menu, wybierz **publikowania CreateExcelWorkbook**. Wykonaj kroki Kreatora publikowania, aby utworzyć zainstalowania wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Kreator publikacji (Office Development w Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Instalowanie aplikacji na komputerze, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.  
  
4.  Po zakończeniu instalacji uruchom zainstalowany program.  
  
5.  Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
 [/ Link (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
