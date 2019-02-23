---
title: 'Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: df22d52ad71b2a98d7e85f4c2002091b97d87b21
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746892"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (C#)
Zestaw lub łączenia Biblioteka dynamiczna (DLL), jest połączony z programu w czasie wykonywania. Aby zademonstrować, tworzenie i używanie biblioteki DLL, należy rozważyć następujący scenariusz:  
  
-   `MathLibrary.DLL`: Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania. W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.  
  
-   `Add`: Plik źródłowy, który zawiera metodę `Add`. Zwraca sumę jego parametrów. Klasa `AddClass` zawierający metody `Add` jest elementem członkowskim przestrzeń nazw `UtilityMethods`.  
  
-   `Mult`: Kod źródłowy, który zawiera metodę `Multiply`. Zwraca iloczyn jego parametrów. Klasa `MultiplyClass` zawierający metody `Multiply` jest również członkiem obszaru nazw `UtilityMethods`.  
  
-   `TestCode`: Plik, który zawiera `Main` metody. Używa metody w pliku DLL do obliczania sumy i produktu argumentów czasu wykonywania.  
  
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
  
 Ten plik zawiera algorytmu, który używa metody biblioteki DLL `Add` i `Multiply`. Zaczyna się od analizowanie argumentów, podane z wiersza polecenia `num1` i `num2`. Następnie suma jest obliczana na podstawie `Add` metody `AddClass` klasy i produkt przy użyciu `Multiply` metody `MultiplyClass` klasy.  
  
 Należy zauważyć, że `using` dyrektywę na początku pliku umożliwia użycie nazwy niekwalifikowanej klas k odkazu metody biblioteki DLL w czasie kompilacji w następujący sposób:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Wykonanie  
 Aby uruchomić program, wprowadź nazwę pliku EXE, a po nim dwóch liczb, w następujący sposób:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby utworzyć plik `MathLibrary.DLL`, skompilować dwa pliki `Add` i `Mult` przy użyciu następującego polecenia.  
  
```csharp  
csc /target:library /out:MathLibrary.DLL Add.cs Mult.cs  
```  
  
 [/Target: Library](../../../../csharp/language-reference/compiler-options/target-library-compiler-option.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL, a nie plikiem EXE. [/Out](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) następuje nazwa pliku — opcja kompilatora służy do określania nazwy pliku biblioteki DLL. W przeciwnym razie kompilator używa pierwszego pliku (`Add.cs`) jako nazwę biblioteki DLL.  
  
 Aby utworzyć plik wykonywalny `TestCode.exe`, użyj następującego polecenia:  
  
```csharp  
csc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.cs  
```  
  
 **/Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`). Ta opcja kompilatora jest opcjonalne. [/Reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane. Aby uzyskać więcej informacji, zobacz [/reference](../../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz [wiersza polecenia tworzenia przy użyciu csc.exe](../../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Tworzenie klasy utrzymującej funkcje DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
