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
ms.openlocfilehash: b84bf20acaaa912e47102973b0484d635f1aa244
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679425"
---
# <a name="main-procedure-in-visual-basic"></a>Procedura główna w Visual Basic
Każda aplikacja w języku Visual Basic mogą zawierać procedury, nazywane `Main`. Ta procedura służy jako początkowy punkt i ogólna kontrola dla danej aplikacji. Wywołania środowiska .NET Framework swoje `Main` procedury po załadowaniu aplikacji i jest gotowy do przekazania do formantu. Jeśli tworzysz aplikację Windows Forms, należy napisać `Main` procedurę dla aplikacji działających w ich własnych.  
  
 `Main` zawiera kod, który jest uruchamiany w pierwszy. W `Main`, można określają formę, która ma być załadowany po raz pierwszy po uruchomieniu programu, sprawdzić, czy kopia aplikacji już działa w systemie, opracowała zestaw zmiennych dla swojej aplikacji lub otworzyć bazy danych, która wymaga aplikacji.  
  
## <a name="requirements-for-the-main-procedure"></a>Wymagania dotyczące procedury głównej  
 Plik, który jest uruchamiany na jego własnej (zwykle z rozszerzeniem .exe) musi zawierać `Main` procedury. Nie działa w jego własnej biblioteki (np. z rozszerzeniem .dll) i nie wymaga `Main` procedury. Wymagania dotyczące różnych typów projektów, że możesz tworzyć są następujące:  
  
-   Aplikacja konsolowa ich własnych i należy podać co najmniej jedną `Main` procedury. .  
  
-   Formularze Windows aplikacje uruchamiane w ich własnych. Jednak kompilator języka Visual Basic automatycznie generuje `Main` procedury w takich aplikacji, a nie trzeba napisać jeden.  
  
-   Biblioteki klas nie wymagają `Main` procedury. Obejmują one bibliotek kontrolek Windows i biblioteki formantów sieci Web. Aplikacje sieci Web są wdrażane jako biblioteki klas.  
  
## <a name="declaring-the-main-procedure"></a>Deklarowanie główne procedury  
 Istnieją cztery sposoby deklarowania `Main` procedury. Czy nie może przebierać argumenty i może zwracać wartość, czy nie.  
  
> [!NOTE]
>  Jeśli zadeklarujesz `Main` w klasie, należy użyć `Shared` — słowo kluczowe. W module `Main` musi być `Shared`.  
  
-   Najprostszym sposobem jest, aby zadeklarować `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` może również zwracać `Integer` wartość, która używa systemu operacyjnego jako kod zakończenia programu. Inne programy można przetestować ten kod, sprawdzając wartość Windows ERRORLEVEL. Aby zwrócić kod wyjścia, należy zadeklarować `Main` jako `Function` procedury zamiast `Sub` procedury.  
  
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
  
-   `Main` może to również przybrać `String` tablic jako argumentu. Każdego ciągu w tablicy zawiera jeden z argumentów wiersza polecenia używane do wywołania programu. Możesz wykonać różne akcje zależnie od ich wartości.  
  
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
  
-   Można zadeklarować `Main` Sprawdź argumenty wiersza polecenia, ale zwraca kod zakończenia, w następujący sposób.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Struktura programu w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String, typ danych](../../../visual-basic/language-reference/data-types/string-data-type.md)
