---
title: "Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d59988ec4899b4115d8d0fd7172e0c8ff8802378
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a><span data-ttu-id="72cba-102">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (C#)</span><span class="sxs-lookup"><span data-stu-id="72cba-102">How to: Create and Use Assemblies Using the Command Line (C#)</span></span>
<span data-ttu-id="72cba-103">Zestaw lub dynamicznej biblioteki połączeń (DLL), jest połączony z programu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72cba-103">An assembly, or a dynamic linking library (DLL), is linked to your program at run time.</span></span> <span data-ttu-id="72cba-104">Aby zademonstrować, tworzenie i używanie biblioteki DLL, rozważmy następujący scenariusz:</span><span class="sxs-lookup"><span data-stu-id="72cba-104">To demonstrate building and using a DLL, consider the following scenario:</span></span>  
  
-   <span data-ttu-id="72cba-105">`MathLibrary.DLL`Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72cba-105">`MathLibrary.DLL`: The library file that contains the methods to be called at run time.</span></span> <span data-ttu-id="72cba-106">W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="72cba-106">In this example, the DLL contains two methods, `Add` and `Multiply`.</span></span>  
  
-   <span data-ttu-id="72cba-107">`Add`Plik źródłowy, który zawiera metodę `Add`.</span><span class="sxs-lookup"><span data-stu-id="72cba-107">`Add`: The source file that contains the method `Add`.</span></span> <span data-ttu-id="72cba-108">Zwraca sumę wartości jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="72cba-108">It returns the sum of its parameters.</span></span> <span data-ttu-id="72cba-109">Klasa `AddClass` zawiera metodę `Add` jest elementem członkowskim przestrzeni nazw `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="72cba-109">The class `AddClass` that contains the method `Add` is a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="72cba-110">`Mult`: Kod źródłowy, który zawiera metodę `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="72cba-110">`Mult`: The source code that contains the method `Multiply`.</span></span> <span data-ttu-id="72cba-111">Zwraca iloczyn jego parametrów.</span><span class="sxs-lookup"><span data-stu-id="72cba-111">It returns the product of its parameters.</span></span> <span data-ttu-id="72cba-112">Klasa `MultiplyClass` zawiera metodę `Multiply` jest również członkiem przestrzeń nazw `UtilityMethods`.</span><span class="sxs-lookup"><span data-stu-id="72cba-112">The class `MultiplyClass` that contains the method `Multiply` is also a member of the namespace `UtilityMethods`.</span></span>  
  
-   <span data-ttu-id="72cba-113">`TestCode`: Plik zawierający `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="72cba-113">`TestCode`: The file that contains the `Main` method.</span></span> <span data-ttu-id="72cba-114">Używa metody w pliku DLL do obliczania sum i produktu argumentów czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72cba-114">It uses the methods in the DLL file to calculate the sum and the product of the run-time arguments.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72cba-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="72cba-115">Example</span></span>  
  
```csharp  
// File: Add.cs   
namespace UtilityMethods  
{  
    public class AddClass   
    {  
        public static long Add(long i, long j)   
        {   
            return (i + j);  
        }  
    }  
}  
```  
  
```csharp  
// File: Mult.cs  
namespace UtilityMethods   
{  
    public class MultiplyClass  
    {  
        public static long Multiply(long x, long y)   
        {  
            return (x * y);   
        }  
    }  
}  
```  
  
```csharp  
// File: TestCode.cs  
  
using UtilityMethods;  
  
class TestCode  
{  
    static void Main(string[] args)   
    {  
        System.Console.WriteLine("Calling methods from MathLibrary.DLL:");  
  
        if (args.Length != 2)  
        {  
            System.Console.WriteLine("Usage: TestCode <num1> <num2>");  
            return;  
        }  
  
        long num1 = long.Parse(args[0]);  
        long num2 = long.Parse(args[1]);  
  
        long sum = AddClass.Add(num1, num2);  
        long product = MultiplyClass.Multiply(num1, num2);  
  
        System.Console.WriteLine("{0} + {1} = {2}", num1, num2, sum);  
        System.Console.WriteLine("{0} * {1} = {2}", num1, num2, product);  
    }  
}  
/* Output (assuming 1234 and 5678 are entered as command-line arguments):  
    Calling methods from MathLibrary.DLL:  
    1234 + 5678 = 6912  
    1234 * 5678 = 7006652          
*/  
```  
  
 <span data-ttu-id="72cba-116">Ten plik zawiera algorytm używa metody DLL `Add` i `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="72cba-116">This file contains the algorithm that uses the DLL methods, `Add` and `Multiply`.</span></span> <span data-ttu-id="72cba-117">Rozpoczyna się analizowanie argumentów wprowadzona w wierszu polecenia `num1` i `num2`.</span><span class="sxs-lookup"><span data-stu-id="72cba-117">It starts with parsing the arguments entered from the command line, `num1` and `num2`.</span></span> <span data-ttu-id="72cba-118">Następnie suma jest obliczana na podstawie `Add` metody na `AddClass` klasy i produktu za pomocą `Multiply` metoda `MultiplyClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="72cba-118">Then it calculates the sum by using the `Add` method on the `AddClass` class, and the product by using the `Multiply` method on the `MultiplyClass` class.</span></span>  
  
 <span data-ttu-id="72cba-119">Zwróć uwagę, że `using` dyrektywy na początku pliku pozwala na użycie nazwy niekwalifikowanej klas do metody DLL referencyjne w czasie kompilacji, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72cba-119">Notice that the `using` directive at the beginning of the file enables you to use the unqualified class names to reference the DLL methods at compile time, as follows:</span></span>  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 <span data-ttu-id="72cba-120">W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72cba-120">Otherwise, you have to use the fully qualified names, as follows:</span></span>  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a><span data-ttu-id="72cba-121">Wykonanie</span><span class="sxs-lookup"><span data-stu-id="72cba-121">Execution</span></span>  
 <span data-ttu-id="72cba-122">Aby uruchomić program, wprowadź nazwę pliku EXE, następuje dwóch liczb w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72cba-122">To run the program, enter the name of the EXE file, followed by two numbers, as follows:</span></span>  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72cba-123">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="72cba-123">Compiling the Code</span></span>  
 <span data-ttu-id="72cba-124">Aby utworzyć plik `MathLibrary.DLL`, Kompiluj dwa pliki `Add` i `Mult` przy użyciu poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="72cba-124">To build the file `MathLibrary.DLL`, compile the two files `Add` and `Mult` by using the following command line.</span></span>  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 <span data-ttu-id="72cba-125">[/Target: Library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL zamiast pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="72cba-125">The [/target:library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) compiler option tells the compiler to output a DLL instead of an EXE file.</span></span> <span data-ttu-id="72cba-126">[/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) następuje nazwa pliku — opcja kompilatora jest używany do określenia nazwy pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="72cba-126">The [/out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) compiler option followed by a file name is used to specify the DLL file name.</span></span> <span data-ttu-id="72cba-127">W przeciwnym razie kompilator używa pierwszego pliku (`Add.cs`) jako nazwę biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="72cba-127">Otherwise, the compiler uses the first file (`Add.cs`) as the name of the DLL.</span></span>  
  
 <span data-ttu-id="72cba-128">Aby utworzyć plik wykonywalny `TestCode.exe`, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="72cba-128">To build the executable file, `TestCode.exe`, use the following command line:</span></span>  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 <span data-ttu-id="72cba-129">**/Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`).</span><span class="sxs-lookup"><span data-stu-id="72cba-129">The **/out** compiler option tells the compiler to output an EXE file and specifies the name of the output file (`TestCode.exe`).</span></span> <span data-ttu-id="72cba-130">Ta opcja kompilatora jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="72cba-130">This compiler option is optional.</span></span> <span data-ttu-id="72cba-131">[/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane.</span><span class="sxs-lookup"><span data-stu-id="72cba-131">The [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option specifies the DLL file or files that this program uses.</span></span> <span data-ttu-id="72cba-132">Aby uzyskać więcej informacji, zobacz [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="72cba-132">For more information, see [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="72cba-133">Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz [kompilowania z wiersza polecenia csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="72cba-133">For more information about building from the command line, see [Command-line Building With csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72cba-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72cba-134">See Also</span></span>  
 [<span data-ttu-id="72cba-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="72cba-135">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="72cba-136">Zestawy i Globalna pamięć podręczna zestawów (C#)</span><span class="sxs-lookup"><span data-stu-id="72cba-136">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="72cba-137">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="72cba-137">Creating a Class to Hold DLL Functions</span></span>](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
