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
# <a name="how-to-create-and-use-assemblies-using-the-command-line-visual-basic"></a>Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (Visual Basic)
Zestaw lub dynamicznej biblioteki połączeń (DLL), jest połączony z programu w czasie wykonywania. Aby zademonstrować, tworzenie i używanie biblioteki DLL, rozważmy następujący scenariusz:  
  
-   `MathLibrary.DLL`Plik biblioteki, który zawiera metody do wywołania w czasie wykonywania. W tym przykładzie biblioteki DLL zawiera dwie metody `Add` i `Multiply`.  
  
-   `Add`Plik źródłowy, który zawiera metodę `Add`. Zwraca sumę wartości jego parametrów. Klasa `AddClass` zawiera metodę `Add` jest elementem członkowskim przestrzeni nazw `UtilityMethods`.  
  
-   `Mult`: Kod źródłowy, który zawiera metodę `Multiply`. Zwraca iloczyn jego parametrów. Klasa `MultiplyClass` zawiera metodę `Multiply` jest również członkiem przestrzeń nazw `UtilityMethods`.  
  
-   `TestCode`: Plik zawierający `Main` metody. Używa metody w pliku DLL do obliczania sum i produktu argumentów czasu wykonywania.  
  
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
  
 Ten plik zawiera algorytm używa metody DLL `Add` i `Multiply`. Rozpoczyna się analizowanie argumentów wprowadzona w wierszu polecenia `num1` i `num2`. Następnie suma jest obliczana na podstawie `Add` metody na `AddClass` klasy i produktu za pomocą `Multiply` metoda `MultiplyClass` klasy.  
  
 Zwróć uwagę, że `Imports` instrukcji na początku pliku pozwala na użycie nazwy niekwalifikowanej klas do metody DLL referencyjne w czasie kompilacji, w następujący sposób:  
  
```vb  
MultiplyClass.Multiply(num1, num2)  
```  
  
 W przeciwnym razie należy użyć w pełni kwalifikowane nazwy w następujący sposób:  
  
```vb  
UtilityMethods.MultiplyClass.Multiply(num1, num2)  
```  
  
## <a name="execution"></a>Wykonanie  
 Aby uruchomić program, wprowadź nazwę pliku EXE, następuje dwóch liczb w następujący sposób:  
  
 `TestCode 1234 5678`  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby utworzyć plik `MathLibrary.DLL`, Kompiluj dwa pliki `Add` i `Mult` przy użyciu poniższego polecenia.  
  
```vb  
vbc /target:library /out:MathLibrary.DLL Add.vb Mult.vb  
```  
  
 [/TARGET (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/target.md) — opcja kompilatora informuje kompilator, aby dane wyjściowe biblioteki DLL zamiast pliku EXE. [/Out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md) następuje nazwa pliku — opcja kompilatora jest używany do określenia nazwy pliku DLL. W przeciwnym razie kompilator używa pierwszego pliku (`Add.vb`) jako nazwę biblioteki DLL.  
  
 Aby utworzyć plik wykonywalny `TestCode.exe`, należy użyć następującego polecenia:  
  
```vb  
vbc /out:TestCode.exe /reference:MathLibrary.DLL TestCode.vb  
```  
  
 **/Out** — opcja kompilatora informuje kompilator, aby dane wyjściowe pliku EXE i określa nazwę pliku wyjściowego (`TestCode.exe`). Ta opcja kompilatora jest opcjonalne. [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora Określa plik DLL lub pliki, które jest używane.  
  
 Aby uzyskać więcej informacji na temat budowania z wiersza polecenia, zobacz i [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Koncepcje programowania](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tworzenie klasy utrzymującej funkcje DLL](../../../../framework/interop/creating-a-class-to-hold-dll-functions.md)
