---
title: Procedura Main
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: cf6003206566dfe8f70a7f75cd4d7ec7565794a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403177"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="cfb87-102">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfb87-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="cfb87-103">Każda aplikacja Visual Basic musi zawierać procedurę o nazwie `Main` .</span><span class="sxs-lookup"><span data-stu-id="cfb87-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="cfb87-104">Ta procedura służy jako punkt wyjścia i ogólna kontrola aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfb87-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="cfb87-105">.NET Framework wywołuje `Main` procedurę po załadowaniu aplikacji i jest gotowa do przekazania kontroli do niej.</span><span class="sxs-lookup"><span data-stu-id="cfb87-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="cfb87-106">Jeśli tworzysz aplikację Windows Forms, musisz napisać `Main` procedurę dla aplikacji, które działają samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="cfb87-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="cfb87-107">`Main`zawiera kod, który jest uruchamiany jako pierwszy.</span><span class="sxs-lookup"><span data-stu-id="cfb87-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="cfb87-108">W programie `Main` można określić, który formularz ma zostać załadowany jako pierwszy podczas uruchamiania programu, sprawdzić, czy kopia aplikacji jest już uruchomiona w systemie, ustalić zestaw zmiennych dla aplikacji lub otworzyć bazę danych wymaganą przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="cfb87-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="cfb87-109">Wymagania dotyczące głównej procedury</span><span class="sxs-lookup"><span data-stu-id="cfb87-109">Requirements for the Main Procedure</span></span>
 <span data-ttu-id="cfb87-110">Plik, który jest uruchamiany samodzielnie (zazwyczaj z rozszerzeniem. exe), musi zawierać `Main` procedurę.</span><span class="sxs-lookup"><span data-stu-id="cfb87-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="cfb87-111">Biblioteka (na przykład z rozszerzeniem dll) nie jest uruchamiana samodzielnie i nie wymaga wykonania `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="cfb87-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="cfb87-112">Poniżej przedstawiono wymagania dotyczące różnych typów projektów, które można utworzyć:</span><span class="sxs-lookup"><span data-stu-id="cfb87-112">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="cfb87-113">Aplikacje konsolowe działają we własnym zakresie i należy podać co najmniej jedną `Main` procedurę.</span><span class="sxs-lookup"><span data-stu-id="cfb87-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="cfb87-114">Windows Forms aplikacje są uruchamiane samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="cfb87-114">Windows Forms applications run on their own.</span></span> <span data-ttu-id="cfb87-115">Jednak kompilator Visual Basic automatycznie generuje `Main` procedurę w takiej aplikacji i nie trzeba jej pisać.</span><span class="sxs-lookup"><span data-stu-id="cfb87-115">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="cfb87-116">Biblioteki klas nie wymagają wykonania `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="cfb87-116">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="cfb87-117">Należą do nich biblioteki formantów systemu Windows i biblioteki formantów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cfb87-117">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="cfb87-118">Aplikacje sieci Web są wdrażane jako biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="cfb87-118">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="cfb87-119">Deklarowanie głównej procedury</span><span class="sxs-lookup"><span data-stu-id="cfb87-119">Declaring the Main Procedure</span></span>
 <span data-ttu-id="cfb87-120">Istnieją cztery sposoby zadeklarować `Main` procedurę.</span><span class="sxs-lookup"><span data-stu-id="cfb87-120">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="cfb87-121">Może przyjmować argumenty i nie może zwracać wartości.</span><span class="sxs-lookup"><span data-stu-id="cfb87-121">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="cfb87-122">Jeśli deklarujesz `Main` w klasie, musisz użyć `Shared` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cfb87-122">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="cfb87-123">W module nie `Main` musi być `Shared` .</span><span class="sxs-lookup"><span data-stu-id="cfb87-123">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="cfb87-124">Najprostszym sposobem jest zadeklarowanie `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="cfb87-124">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="cfb87-125">`Main`może również zwrócić `Integer` wartość, której system operacyjny używa jako kodu zakończenia dla programu.</span><span class="sxs-lookup"><span data-stu-id="cfb87-125">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="cfb87-126">Inne programy mogą testować ten kod, sprawdzając wartość Windows ERRORLEVEL.</span><span class="sxs-lookup"><span data-stu-id="cfb87-126">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="cfb87-127">Aby zwrócić kod zakończenia, należy zadeklarować `Main` jako `Function` procedurę zamiast `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="cfb87-127">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

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

- <span data-ttu-id="cfb87-128">`Main`można również pobrać `String` tablicę jako argument.</span><span class="sxs-lookup"><span data-stu-id="cfb87-128">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="cfb87-129">Każdy ciąg w tablicy zawiera jeden z argumentów wiersza polecenia użytych do wywołania programu.</span><span class="sxs-lookup"><span data-stu-id="cfb87-129">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="cfb87-130">W zależności od ich wartości można wykonać różne akcje.</span><span class="sxs-lookup"><span data-stu-id="cfb87-130">You can take different actions depending on their values.</span></span>

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

- <span data-ttu-id="cfb87-131">Można zadeklarować, `Main` Aby przeanalizować argumenty wiersza polecenia, ale nie zwracać kodu zakończenia w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="cfb87-131">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

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
  
## <a name="see-also"></a><span data-ttu-id="cfb87-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfb87-132">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="cfb87-133">Struktura programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfb87-133">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="cfb87-134">-main</span><span class="sxs-lookup"><span data-stu-id="cfb87-134">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="cfb87-135">Shared</span><span class="sxs-lookup"><span data-stu-id="cfb87-135">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="cfb87-136">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cfb87-136">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="cfb87-137">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cfb87-137">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="cfb87-138">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="cfb87-138">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="cfb87-139">Typ danych ciągu</span><span class="sxs-lookup"><span data-stu-id="cfb87-139">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
