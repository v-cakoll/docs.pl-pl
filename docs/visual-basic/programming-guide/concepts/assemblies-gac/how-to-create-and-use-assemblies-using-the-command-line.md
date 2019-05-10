---
title: 'Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (Visual Basic)'
ms.date: 03/14/2018
ms.assetid: 229ff9fb-1bd1-403b-946b-526104864c60
ms.openlocfilehash: d58109dfbb03b752f4a46f895fa1093e4f37df71
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624768"
---
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Instrukcje: Tworzenie i używanie zestawów przy użyciu wiersza polecenia (Visual Basic)
Zestaw lub łączenia Biblioteka dynamiczna (DLL), jest połączony z programu w czasie wykonywania. Aby zademonstrować, tworzenie i używanie biblioteki DLL, należy rozważyć następujący scenariusz:  
  
- `MathLibrary.DLL`: Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania. W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.  
  
- `Add`: Plik źródłowy, który zawiera metodę `Add`. Zwraca sumę jego parametrów. Klasa `AddClass` zawierający metody `Add` jest elementem członkowskim przestrzeń nazw `UtilityMethods`.  
  
- `Mult`: Kod źródłowy, który zawiera metodę `Multiply`. Zwraca iloczyn jego parametrów. Klasa `MultiplyClass` zawierający metody `Multiply` jest również członkiem obszaru nazw `UtilityMethods`.  
  
- `TestCode`: Plik, który zawiera `Main` metody. Używa metody w pliku DLL do obliczania sumy i produktu argumentów czasu wykonywania.  
  
## <a name="example"></a>Przykład  
  
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
  
 Ten plik zawiera algorytmu, który używa metody biblioteki DLL `Add` i `Multiply`. Zaczyna się od analizowanie argumentów, podane z wiersza polecenia `num1` i `num2`. Następnie suma jest obliczana na podstawie `Add` metody `AddClass` klasy i produkt przy użyciu `Multiply` metody `MultiplyClass` klasy.  
  
 Należy zauważyć, że `Imports` instrukcji na początku pliku umożliwia użycie nazwy niekwalifikowanej klas k odkazu metody biblioteki DLL w czasie kompilacji w następujący sposób:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Wykonanie  
 Aby uruchomić program, wprowadź nazwę pliku EXE, a po nim dwóch liczb, w następujący sposób:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby utworzyć plik `MathLibrary.DLL`, skompilować dwa pliki `Add` i `Mult` przy użyciu następującego polecenia.  
  
```console  
vbc -target:library -out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [-Target (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL, a nie plikiem EXE. [-Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) następuje nazwa pliku — opcja kompilatora służy do określania nazwy pliku biblioteki DLL. W przeciwnym razie kompilator używa pierwszego pliku (`Add.vb`) jako nazwę biblioteki DLL.  
  
 Aby utworzyć plik wykonywalny `TestCode.exe`, użyj następującego polecenia:  
  
```console  
vbc -out:TestCode.exe -reference:MathLibrary.DLL TestCode.vb  
```  
  
 **-Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`). Ta opcja kompilatora jest opcjonalne. [— Odwołanie (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane.  
  
 Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz i [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
- [Zestawy w środowisku .NET](../../../../standard/assembly/index.md)
- [Tworzenie klasy utrzymującej funkcje DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
