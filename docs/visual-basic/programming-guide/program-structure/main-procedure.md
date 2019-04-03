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
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833675"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="dd8cf-102">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd8cf-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="dd8cf-103">Każda aplikacja w języku Visual Basic mogą zawierać procedury, nazywane `Main`.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="dd8cf-104">Ta procedura służy jako początkowy punkt i ogólna kontrola dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="dd8cf-105">Wywołania środowiska .NET Framework swoje `Main` procedury po załadowaniu aplikacji i jest gotowy do przekazania do formantu.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="dd8cf-106">Jeśli tworzysz aplikację Windows Forms, należy napisać `Main` procedurę dla aplikacji działających w ich własnych.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="dd8cf-107">`Main` zawiera kod, który jest uruchamiany w pierwszy.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="dd8cf-108">W `Main`, można określają formę, która ma być załadowany po raz pierwszy po uruchomieniu programu, sprawdzić, czy kopia aplikacji już działa w systemie, opracowała zestaw zmiennych dla swojej aplikacji lub otworzyć bazy danych, która wymaga aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="dd8cf-109">Wymagania dotyczące procedury głównej</span><span class="sxs-lookup"><span data-stu-id="dd8cf-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="dd8cf-110">Plik, który jest uruchamiany na jego własnej (zwykle z rozszerzeniem .exe) musi zawierać `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="dd8cf-111">Nie działa w jego własnej biblioteki (np. z rozszerzeniem .dll) i nie wymaga `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="dd8cf-112">Wymagania dotyczące różnych typów projektów, że możesz tworzyć są następujące:</span><span class="sxs-lookup"><span data-stu-id="dd8cf-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="dd8cf-113">Aplikacja konsolowa ich własnych i należy podać co najmniej jedną `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="dd8cf-114">.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-114">.</span></span>  
  
-   <span data-ttu-id="dd8cf-115">Formularze Windows aplikacje uruchamiane w ich własnych.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="dd8cf-116">Jednak kompilator języka Visual Basic automatycznie generuje `Main` procedury w takich aplikacji, a nie trzeba napisać jeden.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="dd8cf-117">Biblioteki klas nie wymagają `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="dd8cf-118">Obejmują one bibliotek kontrolek Windows i biblioteki formantów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="dd8cf-119">Aplikacje sieci Web są wdrażane jako biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="dd8cf-120">Deklarowanie główne procedury</span><span class="sxs-lookup"><span data-stu-id="dd8cf-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="dd8cf-121">Istnieją cztery sposoby deklarowania `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="dd8cf-122">Czy nie może przebierać argumenty i może zwracać wartość, czy nie.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd8cf-123">Jeśli zadeklarujesz `Main` w klasie, należy użyć `Shared` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="dd8cf-124">W module `Main` musi być `Shared`.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="dd8cf-125">Najprostszym sposobem jest, aby zadeklarować `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="dd8cf-126">`Main` może również zwracać `Integer` wartość, która używa systemu operacyjnego jako kod zakończenia programu.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="dd8cf-127">Inne programy można przetestować ten kod, sprawdzając wartość Windows ERRORLEVEL.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="dd8cf-128">Aby zwrócić kod wyjścia, należy zadeklarować `Main` jako `Function` procedury zamiast `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
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
  
-   <span data-ttu-id="dd8cf-129">`Main` może to również przybrać `String` tablic jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="dd8cf-130">Każdego ciągu w tablicy zawiera jeden z argumentów wiersza polecenia używane do wywołania programu.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="dd8cf-131">Możesz wykonać różne akcje zależnie od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-131">You can take different actions depending on their values.</span></span>  
  
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
  
-   <span data-ttu-id="dd8cf-132">Można zadeklarować `Main` Sprawdź argumenty wiersza polecenia, ale zwraca kod zakończenia, w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="dd8cf-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd8cf-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd8cf-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="dd8cf-134">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd8cf-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="dd8cf-135">/main</span><span class="sxs-lookup"><span data-stu-id="dd8cf-135">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="dd8cf-136">Shared</span><span class="sxs-lookup"><span data-stu-id="dd8cf-136">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="dd8cf-137">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dd8cf-137">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="dd8cf-138">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="dd8cf-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="dd8cf-139">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="dd8cf-139">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="dd8cf-140">String, typ danych</span><span class="sxs-lookup"><span data-stu-id="dd8cf-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
