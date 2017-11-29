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
# <a name="walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-visual-studio-visual-basic"></a>Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (Visual Basic)
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
  
4.  Otwórz menu skrótów projektu CreateExcelWorkbook, a następnie wybierz pozycję **właściwości**. Wybierz **odwołania** kartę. Wybierz **Dodaj** przycisku.  
  
5.  Na **.NET** , wybierz pozycję najnowszą wersję `Microsoft.Office.Interop.Excel`. Na przykład **Microsoft.Office.Interop.Excel 14.0.0.0**. Wybierz **OK** przycisku.  
  
6.  Na liście odwołań dla **CreateExcelWorkbook** projektu, zaznacz odwołanie `Microsoft.Office.Interop.Excel` dodanym w poprzednim kroku. W **właściwości** okna, upewnij się, że `Embed Interop Types` właściwość jest ustawiona na `True`.  
  
    > [!NOTE]
    >  Z powodu osadzony typ międzyoperacyjny informacji o różnych wersjach pakietu Microsoft Office jest uruchomiona aplikacja utworzone w tym przewodniku. Jeśli `Embed Interop Types` właściwość jest ustawiona na `False`, musi zawierać PIA dla każdej wersji pakietu Microsoft Office, aplikacja będzie uruchamiana z.  
  
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
  
##  <a name="BKMK_publishapp"></a>Aby opublikować aplikację na komputerze, na którym zainstalowany jest inna wersja programu Microsoft Office  
  
1.  Otwórz projekt utworzone przez tego przewodnika w programie Visual Studio.  
  
2.  Na **kompilacji** menu, wybierz **publikowania CreateExcelWorkbook**. Wykonaj kroki Kreatora publikowania, aby utworzyć zainstalowania wersji aplikacji. Aby uzyskać więcej informacji, zobacz [Kreator publikacji (Office Development w Visual Studio)](https://msdn.microsoft.com/library/bb625071).  
  
3.  Instalowanie aplikacji na komputerze, na którym zainstalowano .NET Framework 4 lub nowszym i różnych wersji programu Excel.  
  
4.  Po zakończeniu instalacji uruchom zainstalowany program.  
  
5.  Sprawdź, czy skoroszyt programu Excel została utworzona w lokalizacji określonej w przykładowym kodzie: C:\SampleFolder\SampleWorkbook.xls.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [/ Link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)
