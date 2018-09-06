---
title: 'Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)'
ms.date: 07/20/2015
ms.assetid: 3320e866-01f1-4b7f-8932-049a7b2d2a9b
ms.openlocfilehash: 381173eedc209930e011dfa7f1711167f16d5ef6
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890717"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-c"></a>Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)
Jeśli informacje o typie jest osadzony w aplikacji, która odwołuje się do obiektów COM, można wyeliminować potrzebę zestawu podstawowej usługi międzyoperacyjnej (PIA). Ponadto informacje o typie osadzony umożliwia osiągnąć niezależność Twojej aplikacji. Oznacza to by używał typów z wielu wersji biblioteki COM bez konieczności określonego PIA dla każdej wersji można napisać program. Jest to typowy scenariusz w przypadku aplikacji korzystających z bibliotek Microsoft Office obiektów. Osadzanie informacji o typie umożliwia tym samym kompilację programu do pracy z różnymi wersjami pakietu Microsoft Office na różnych komputerach bez konieczności ponownego wdrażania programu lub PIA dla każdej wersji pakietu Microsoft Office.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Ten przewodnik wymaga następujących elementów:  
  
-   Komputer, na którym zainstalowano program Visual Studio i programu Microsoft Excel.  
  
-   Drugi komputer, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.  
  
##  <a name="BKMK_createapp"></a> Aby utworzyć aplikację, która działa z wieloma wersjami pakietu Microsoft Office  
  
1.  Uruchom program Visual Studio na komputerze, na którym zainstalowany jest program Excel.  
  
2.  Na **pliku** menu, wybierz **New**, **projektu**.  
  
3.  W **nowy projekt** dialogowym **typów projektów** okienka, upewnij się, że **Windows** jest zaznaczone. Wybierz **aplikację Konsolową** w **szablony** okienka. W **nazwa** wprowadź `CreateExcelWorkbook`, a następnie wybierz **OK** przycisku. Nowy projekt zostanie utworzony.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **odwołania** folder, a następnie wybierz **Dodaj odwołanie**.  
  
5.  Na **.NET** karty, wybierz najnowszą wersję `Microsoft.Office.Interop.Excel`. Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**. Wybierz **OK** przycisku.  
  
6.  Na liście odwołań dla **CreateExcelWorkbook** projektu, wybierz odwołanie do `Microsoft.Office.Interop.Excel` dodanej w poprzednim kroku. W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.  
  
    > [!NOTE]
    >  Aplikacja utworzona w tym instruktażu działa z różnymi wersjami pakietu Microsoft Office z powodu informacji osadzonego typu międzyoperacyjnego. Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, należy uwzględnić PIA dla każdej wersji pakietu Microsoft Office, aplikacja zostanie uruchomiona przy użyciu.  
  
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
  
##  <a name="BKMK_publishapp"></a> Aby opublikować aplikację na komputerze, na którym zainstalowano inną wersję programu Microsoft Office  
  
1.  Otwórz projekt utworzony w tym instruktażu w programie Visual Studio.  
  
2.  Na **kompilacji** menu, wybierz **Publikuj CreateExcelWorkbook**. Wykonaj kroki Kreatora publikacji, aby utworzyć instalowalną wersję aplikacji. Aby uzyskać więcej informacji, zobacz [Kreatora publikacji (Office Development w programie Visual Studio)](/visualstudio/vsto/publish-wizard-office-development-in-visual-studio).  
  
3.  Zainstaluj aplikację na komputerze, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.  
  
4.  Po zakończeniu instalacji uruchom zainstalowany program.  
  
5.  Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)  
- [/ Link (opcje kompilatora C#)](../../../../csharp/language-reference/compiler-options/link-compiler-option.md)
