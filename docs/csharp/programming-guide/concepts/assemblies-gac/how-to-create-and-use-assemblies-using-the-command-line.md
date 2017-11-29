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
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (C#)
Zestaw lub dynamicznej biblioteki połączeń (DLL), jest połączony z programu w czasie wykonywania. Aby zademonstrować, tworzenie i używanie biblioteki DLL, rozważmy następujący scenariusz:  
  
-   `MathLibrary.DLL`Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania. W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.  
  
-   `Add`Plik źródłowy, który zawiera metodę `Add`. Zwraca sumę wartości jego parametrów. Klasa `AddClass` zawiera metodę `Add` jest elementem członkowskim przestrzeni nazw `UtilityMethods`.  
  
-   `Mult`: Kod źródłowy, który zawiera metodę `Multiply`. Zwraca iloczyn jego parametrów. Klasa `MultiplyClass` zawiera metodę `Multiply` jest również członkiem przestrzeń nazw `UtilityMethods`.  
  
-   `TestCode`: Plik zawierający `Main` metody. Używa metody w pliku DLL do obliczania sum i produktu argumentów czasu wykonywania.  
  
## <a name="example"></a>Przykład  
  
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
  
 Ten plik zawiera algorytm używa metody DLL `Add` i `Multiply`. Rozpoczyna się analizowanie argumentów wprowadzona w wierszu polecenia `num1` i `num2`. Następnie suma jest obliczana na podstawie `Add` metody na `AddClass` klasy i produktu za pomocą `Multiply` metoda `MultiplyClass` klasy.  
  
 Zwróć uwagę, że `using` dyrektywy na początku pliku pozwala na użycie nazwy niekwalifikowanej klas do metody DLL referencyjne w czasie kompilacji, w następujący sposób:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Wykonanie  
 Aby uruchomić program, wprowadź nazwę pliku EXE, następuje dwóch liczb w następujący sposób:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby utworzyć plik `MathLibrary.DLL`, Kompiluj dwa pliki `Add` i `Mult` przy użyciu poniższego polecenia.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: Library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL zamiast pliku EXE. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) następuje nazwa pliku — opcja kompilatora jest używany do określenia nazwy pliku DLL. W przeciwnym razie kompilator używa pierwszego pliku (`Add.cs`) jako nazwę biblioteki DLL.  
  
 Aby utworzyć plik wykonywalny `TestCode.exe`, należy użyć następującego polecenia:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`). Ta opcja kompilatora jest opcjonalne. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane. Aby uzyskać więcej informacji, zobacz [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz [kompilowania z wiersza polecenia csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Tworzenie klasy utrzymującej funkcje DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
