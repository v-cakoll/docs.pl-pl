---
title: "Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 72f3e91f9fb88019f937dcd281aa14ab4e887daf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a><span data-ttu-id="13848-102">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13848-102">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>
<span data-ttu-id="13848-103">Zestaw lub dynamicznej biblioteki połączeń (DLL), jest połączony z programu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13848-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="13848-104">Aby zademonstrować, tworzenie i używanie biblioteki DLL, rozważmy następujący scenariusz:</span><span class="sxs-lookup"><span data-stu-id="13848-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="13848-105">`MathLibrary.DLL`Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13848-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="13848-106">W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="13848-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="13848-107">`Add`Plik źródłowy, który zawiera metodę `Add`.</span><span class="sxs-lookup"><span data-stu-id="13848-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="13848-108">Zwraca sumę wartości jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="13848-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="13848-109">Klasa `AddClass` zawiera metodę `Add` jest elementem członkowskim przestrzeni nazw `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="13848-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="13848-110">`Mult`: Kod źródłowy, który zawiera metodę `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="13848-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="13848-111">Zwraca iloczyn jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="13848-111">It returns the product of its parameters.</span></span> <span data-ttu-id="13848-112">Klasa `MultiplyClass` zawiera metodę `Multiply` jest również członkiem przestrzeń nazw `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="13848-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="13848-113">`TestCode`: Plik zawierający `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="13848-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="13848-114">Używa metody w pliku DLL do obliczania sum i produktu argumentów czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="13848-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13848-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="13848-115">Example</span></span>  
  
```vb  
' File: Add.vb   
Namespace UtilityMethods  
    Public Class AddClass  
        Public Shared Function Add(ByVal i As Long, ByVal j As Long) As Long  
            Return i + j  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: Mult.vb  
Namespace UtilityMethods  
    Public Class MultiplyClass  
        Public Shared Function Multiply(ByVal x As Long, ByVal y As Long) As Long  
            Return x * y  
        End Function  
    End Class  
End Namespace  
```  
  
```vb  
' File: TestCode.vb  
  
Imports UtilityMethods  
  
Module Test  
  
    Sub Main(ByVal args As String())  
  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:")  
  
        If args.Length <> 2 Then  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>")  
            Return  
        End If  
  
        Dim num1 As Long = Long.Parse(args(0))  
        Dim num2 As Long = Long.Parse(args(1))  
  
        Dim sum As Long = AddClass.Add(num1, num2)  
        Dim product As Long = MultiplyClass.Multiply(num1, num2)  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum)  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product)  
  
    End Sub  
  
End Module  
  
' Output (assuming 1234 and 5678 are entered as command-line arguments):  
' Calling methods from MathLibrary.DLL:  
' 1234 + 5678 = 6912  
' 1234 * 5678 = 7006652  
```  
  
 <span data-ttu-id="13848-116">Ten plik zawiera algorytm używa metody DLL `Add` i `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="13848-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="13848-117">Rozpoczyna się analizowanie argumentów wprowadzona w wierszu polecenia `num1` i `num2`.</span><span class="sxs-lookup"><span data-stu-id="13848-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="13848-118">Następnie suma jest obliczana na podstawie `Add` metody na `AddClass` klasy i produktu za pomocą `Multiply` metoda `MultiplyClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="13848-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="13848-119">Zwróć uwagę, że `Imports` instrukcji na początku pliku pozwala na użycie nazwy niekwalifikowanej klas do metody DLL referencyjne w czasie kompilacji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="13848-119">Notice that the  `Imports` statement at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 <span data-ttu-id="13848-120">W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="13848-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a><span data-ttu-id="13848-121">Wykonanie</span><span class="sxs-lookup"><span data-stu-id="13848-121">Execution</span></span>  
 <span data-ttu-id="13848-122">Aby uruchomić program, wprowadź nazwę pliku EXE, następuje dwóch liczb w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="13848-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13848-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="13848-123">Compiling the Code</span></span>  
 <span data-ttu-id="13848-124">Aby utworzyć plik `MathLibrary.DLL`, Kompiluj dwa pliki `Add` i `Mult` przy użyciu poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="13848-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 <span data-ttu-id="13848-125">[/TARGET (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL zamiast pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="13848-125">The [/target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="13848-126">[/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) następuje nazwa pliku — opcja kompilatora jest używany do określenia nazwy pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="13848-126">The [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="13848-127">W przeciwnym razie kompilator używa pierwszego pliku (`Add.vb`) jako nazwę biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="13848-127">Otherwise, the compiler uses the first file (`Add.vb`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="13848-128">Aby utworzyć plik wykonywalny `TestCode.exe`, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="13848-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 <span data-ttu-id="13848-129">**/Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="13848-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="13848-130">Ta opcja kompilatora jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="13848-130">This compiler option is optional.</span></span> <span data-ttu-id="13848-131">[/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane.</span><span class="sxs-lookup"><span data-stu-id="13848-131">The [/reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) compiler option specifies the DLL file or files that this program uses.</span></span>  
  
 <span data-ttu-id="13848-132">Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz i [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="13848-132">For more information about building from the command line, see  and [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13848-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13848-133">See Also</span></span>  
 [<span data-ttu-id="13848-134">Koncepcje programowania</span><span class="sxs-lookup"><span data-stu-id="13848-134">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="13848-135">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13848-135">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="13848-136">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="13848-136">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
