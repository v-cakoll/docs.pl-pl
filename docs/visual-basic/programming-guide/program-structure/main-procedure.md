---
title: "Procedura główna w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6de98ad4e470cd0becaf25f5a9a00c8095e44b15
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="main-procedure-in-visual-basic"></a>Procedura główna w Visual Basic
Każda aplikacja Visual Basic musi zawierać wywołuje procedurę `Main`. Ta procedura służy jako początkowy punkt i ogólnej kontroli aplikacji. Wywołania .NET Framework z `Main` procedury po załadowaniu aplikacji i jest gotowy do przekazania do formantu. Jeśli tworzysz aplikacji formularzy systemu Windows, należy napisać `Main` procedury dla aplikacji działających na ich własnych.  
  
 `Main`zawiera kod, który jest uruchamiany pierwszy. W `Main`, można określić postać, która ma być załadowany najpierw, po uruchomieniu programu, dowiedzieć się, czy kopia aplikacji już działa w systemie, ustanowić zestaw zmiennych dla aplikacji lub otworzyć bazy danych, która wymaga aplikacji.  
  
## <a name="requirements-for-the-main-procedure"></a>Wymagania dotyczące procedury głównej  
 Plik, który jest uruchamiany na jego własnej (zwykle z rozszerzeniem .exe) musi zawierać `Main` procedury. Nie działa w jego własnej biblioteki (na przykład z rozszerzeniem dll) i nie wymaga `Main` procedury. Wymagania dla różnych typów projektów można utworzyć są następujące:  
  
-   Aplikacje konsoli Uruchom na ich własnych i musisz podać co najmniej jeden `Main` procedury. .  
  
-   Uruchom ich własnych aplikacji formularzy systemu Windows. Jednak kompilator Visual Basic automatycznie generuje `Main` procedury w taki aplikacji, a nie trzeba zapisać jeden.  
  
-   Biblioteki klas nie wymagają `Main` procedury. Obejmują one biblioteki formantów systemu Windows i biblioteki formantów sieci Web. Aplikacje sieci Web są wdrażane jako biblioteki klas.  
  
## <a name="declaring-the-main-procedure"></a>Deklarowanie procedury głównej  
 Istnieją cztery metody, aby zadeklarować `Main` procedury. Lub nie może upłynąć argumentów i lub nie może zwracać wartości.  
  
> [!NOTE]
>  W przypadku `Main` w klasie, należy użyć `Shared` — słowo kluczowe. W module `Main` musi być `Shared`.  
  
-   Najprostszym sposobem jest zadeklarować `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main`można także wrócić `Integer` wartość, która korzysta z systemu operacyjnego jako kod zakończenia programu do. Inne programy można przetestować tego kodu, sprawdzając wartość ERRORLEVEL systemu Windows. Aby przywrócić kod zakończenia, należy zadeklarować `Main` jako `Function` procedury zamiast `Sub` procedury.  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main`możliwe jest również `String` tablic jako argumentu. Każdy ciąg w tablicy zawiera jeden z argumentów wiersza polecenia używane do wywołania programu. Można wykonać różne akcje zależnie od ich wartości.  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   Można zadeklarować `Main` do zbadania argumenty wiersza polecenia, ale zwraca kod zakończenia w następujący sposób.  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)
