---
title: Procedura główna w Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 19c6fcb04a373d782db3deafc732f69bf20e7f0e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962773"
---
# <a name="main-procedure-in-visual-basic"></a>Procedura główna w Visual Basic
Każda aplikacja Visual Basic musi zawierać procedurę o nazwie `Main`. Ta procedura służy jako punkt wyjścia i ogólna kontrola aplikacji. .NET Framework wywołuje `Main` procedurę po załadowaniu aplikacji i jest gotowa do przekazania kontroli do niej. Jeśli tworzysz aplikację Windows Forms, musisz napisać `Main` procedurę dla aplikacji, które działają samodzielnie.

 `Main`zawiera kod, który jest uruchamiany jako pierwszy. W `Main`programie można określić, który formularz ma zostać załadowany jako pierwszy podczas uruchamiania programu, sprawdzić, czy kopia aplikacji jest już uruchomiona w systemie, ustalić zestaw zmiennych dla aplikacji lub otworzyć bazę danych wymaganą przez aplikację.

## <a name="requirements-for-the-main-procedure"></a>Wymagania dotyczące głównej procedury
 Plik, który jest uruchamiany samodzielnie (zazwyczaj z rozszerzeniem. exe), `Main` musi zawierać procedurę. Biblioteka (na przykład z rozszerzeniem dll) nie jest uruchamiana samodzielnie i nie wymaga `Main` wykonania procedury. Poniżej przedstawiono wymagania dotyczące różnych typów projektów, które można utworzyć:

- Aplikacje konsolowe działają we własnym zakresie i należy podać co najmniej jedną `Main` procedurę.

- Windows Forms aplikacje są uruchamiane samodzielnie. Jednak kompilator Visual Basic automatycznie generuje `Main` procedurę w takiej aplikacji i nie trzeba jej pisać.

- Biblioteki klas nie wymagają `Main` wykonania procedury. Należą do nich biblioteki formantów systemu Windows i biblioteki formantów sieci Web. Aplikacje sieci Web są wdrażane jako biblioteki klas.

## <a name="declaring-the-main-procedure"></a>Deklarowanie głównej procedury
 Istnieją cztery sposoby zadeklarować `Main` procedurę. Może przyjmować argumenty i nie może zwracać wartości.

> [!NOTE]
> Jeśli deklarujesz `Main` w klasie, musisz `Shared` użyć słowa kluczowego. W module `Main` nie musi być `Shared`.

- Najprostszym sposobem jest zadeklarowanie `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`może również zwrócić `Integer` wartość, której system operacyjny używa jako kodu zakończenia dla programu. Inne programy mogą testować ten kod, sprawdzając wartość Windows ERRORLEVEL. Aby zwrócić kod zakończenia, należy zadeklarować `Main` `Function` jako procedurę zamiast `Sub` procedury.

    ```vb
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

- `Main`można również pobrać `String` tablicę jako argument. Każdy ciąg w tablicy zawiera jeden z argumentów wiersza polecenia użytych do wywołania programu. W zależności od ich wartości można wykonać różne akcje.

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
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

- Można zadeklarować `Main` , aby przeanalizować argumenty wiersza polecenia, ale nie zwracać kodu zakończenia w następujący sposób.

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Struktura programu Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)
