---
title: 'Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 26b44286-5066-4ad4-8e6a-c24902be347c
ms.openlocfilehash: 6a28e95f9c3cfcc2481c8f4f9f83303648df43cd
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244056"
---
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)
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
  
4.  Otwórz menu skrótów projektu CreateExcelWorkbook, a następnie wybierz **właściwości**. Wybierz **odwołania** kartę. Wybierz **Dodaj** przycisku.  
  
5.  Na **.NET** karty, wybierz najnowszą wersję `Microsoft.Office.Interop.Excel`. Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**. Wybierz **OK** przycisku.  
  
6.  Na liście odwołań dla **CreateExcelWorkbook** projektu, wybierz odwołanie do `Microsoft.Office.Interop.Excel` dodanej w poprzednim kroku. W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.  
  
    > [!NOTE]
    >  Aplikacja utworzona w tym instruktażu działa z różnymi wersjami pakietu Microsoft Office z powodu informacji osadzonego typu międzyoperacyjnego. Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, należy uwzględnić PIA dla każdej wersji pakietu Microsoft Office, aplikacja zostanie uruchomiona przy użyciu.  
  
7.  Otwórz plik Module1.vb. Zastąp kod w pliku następującym kodem:  
  
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
  
8.  Zapisz projekt.  
  
9. Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić projekt. Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
##  <a name="BKMK_publishapp"></a> Aby opublikować aplikację na komputerze, na którym zainstalowano inną wersję programu Microsoft Office  
  
1.  Otwórz projekt utworzony w tym instruktażu w programie Visual Studio.  
  
2.  Na **kompilacji** menu, wybierz **Publikuj CreateExcelWorkbook**. Wykonaj kroki Kreatora publikacji, aby utworzyć instalowalną wersję aplikacji. Aby uzyskać więcej informacji, zobacz [Kreatora publikacji (Office Development w programie Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Zainstaluj aplikację na komputerze, na którym są zainstalowane .NET Framework 4 lub nowszy oraz różne wersje programu Excel.  
  
4.  Po zakończeniu instalacji uruchom zainstalowany program.  
  
5.  Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
