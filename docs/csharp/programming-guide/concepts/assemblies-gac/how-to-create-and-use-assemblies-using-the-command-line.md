---
title: 'Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (C#)'
ms.date: 07/20/2015
ms.assetid: 408ddce3-89e3-4e12-8353-34a49beeb72b
ms.openlocfilehash: 0a8db22a05d834d15f6e6b7f049f59f86bc1fe1d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595962"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-c"></a>Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (C#)
Zestaw lub biblioteka dołączana dynamicznie (DLL) jest połączony z programem w czasie wykonywania. Aby zademonstrować Kompilowanie i korzystanie z biblioteki DLL, należy wziąć pod uwagę następujący scenariusz:  
  
- `MathLibrary.DLL`: Plik biblioteki zawierający metody do wywołania w czasie wykonywania. W tym przykładzie biblioteka DLL zawiera dwie metody `Add` i. `Multiply`  
  
- `Add`: Plik źródłowy, który zawiera metodę `Add`. Zwraca sumę jego parametrów. Klasa `AddClass` , która zawiera metodę `Add` , należy do przestrzeni nazw `UtilityMethods`.  
  
- `Mult`: Kod źródłowy, który zawiera metodę `Multiply`. Zwraca iloczyn jego parametrów. Klasa `MultiplyClass` , która zawiera metodę `Multiply` , jest również składową przestrzeni nazw `UtilityMethods`.  
  
- `TestCode`: Plik, który zawiera `Main` metodę. Używa metod w pliku DLL, aby obliczyć sumę i iloczyn argumentów czasu wykonywania.  
  
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
  
 Ten plik zawiera algorytm korzystający z metod `Add` dll i. `Multiply` Rozpoczyna się od analizy argumentów wprowadzonych z wiersza `num1` polecenia i. `num2` Następnie oblicza sumę przy `Add` użyciu metody `AddClass` klasy i produktu przy `MultiplyClass` użyciu `Multiply` metody klasy.  
  
 Należy zauważyć, `using` że dyrektywa na początku pliku umożliwia użycie niekwalifikowanych nazw klas do odwoływania się do metod biblioteki DLL w czasie kompilacji w następujący sposób:  
  
```csharp  
MultiplyClass.Multiply(num1, num2);  
```  
  
 W przeciwnym razie musisz użyć w pełni kwalifikowanych nazw w następujący sposób:  
  
```csharp  
UtilityMethods.MultiplyClass.Multiply(num1, num2);  
```  
  
## <a name="execution"></a>Wykonanie  
 Aby uruchomić program, wprowadź nazwę pliku EXE, a następnie dwie cyfry w następujący sposób:  
  
 `TestCode 1234 5678`  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Tworzenie klasy utrzymującej funkcje DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
