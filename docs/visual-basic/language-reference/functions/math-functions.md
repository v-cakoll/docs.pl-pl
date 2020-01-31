---
title: Funkcje matematyczne
ms.date: 01/27/2020
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: ea30ae3b30484c1a13d6d540f121c03afb30ba26
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794594"
---
# <a name="math-functions-visual-basic"></a>Funkcje matematyczne (Visual Basic)

Metody klasy <xref:System.Math?displayProperty=nameWithType> zapewniają trygonometryczne, logarytmiczne i inne typowe funkcje matematyczne.

## <a name="remarks"></a>Uwagi

W poniższej tabeli wymieniono metody klasy <xref:System.Math?displayProperty=nameWithType>. Można ich użyć w Visual Basic programie:
  
|Metoda .NET|Opis|
|---------------------------|-----------------|
|<xref:System.Math.Abs%2A>|Zwraca wartość bezwzględną liczby.|
|<xref:System.Math.Acos%2A>|Zwraca kąt, którego cosinus jest równy podanej liczbie.|
|<xref:System.Math.Asin%2A>|Zwraca kąt, którego sinus jest równy podanej liczbie.|
|<xref:System.Math.Atan%2A>|Zwraca kąt, którego tangens jest równy podanej liczbie.|
|<xref:System.Math.Atan2%2A>|Zwraca kąt, którego tangens jest ilorazem dwóch określonych liczb.|
|<xref:System.Math.BigMul%2A>|Zwraca pełny iloczyn liczby 2 32-bitowych.|
|<xref:System.Math.Ceiling%2A>|Zwraca najmniejszą wartość całkowitą, która jest większa lub równa określonej `Decimal` lub `Double`.|
|<xref:System.Math.Cos%2A>|Zwraca cosinus określonego kąta.|
|<xref:System.Math.Cosh%2A>|Zwraca cosinus hiperboliczny odpowiadający podanemu kątowi.|
|<xref:System.Math.DivRem%2A>|Zwraca iloraz 2 32-bitowych lub 64-bitowych liczb całkowitych ze znakiem, a także Zwraca resztę z parametru wyjściowego.|
|<xref:System.Math.Exp%2A>|Zwraca wartość e (podstawę logarytmów naturalnych) podniesioną do określonej potęgi.|
|<xref:System.Math.Floor%2A>|Zwraca największą liczbę całkowitą, która jest mniejsza lub równa podanemu `Decimal` lub `Double`.|
|<xref:System.Math.IEEERemainder%2A>|Zwraca resztę z dzielenia przez określony numer przez inny określony numer.|
|<xref:System.Math.Log%2A>|Zwraca logarytm naturalny (o podstawie e) podanej liczby lub logarytm o określonym numerze w określonej bazie.|
|<xref:System.Math.Log10%2A>|Zwraca logarytm dziesiętny z podanej liczby.|
|<xref:System.Math.Max%2A>|Zwraca większą liczbę dwóch liczb.|
|<xref:System.Math.Min%2A>|Zwraca mniejsze z dwóch liczb.|
|<xref:System.Math.Pow%2A>|Zwraca określoną liczbę podniesioną do określonej potęgi.|
|<xref:System.Math.Round%2A>|Zwraca wartość `Decimal` lub `Double` zaokrągloną do najbliższej wartości całkowitej lub do określonej liczby cyfr ułamkowych.|
|<xref:System.Math.Sign%2A>|Zwraca wartość `Integer` wskazującą znak liczby.|
|<xref:System.Math.Sin%2A>|Zwraca sinus określonego kąta.|
|<xref:System.Math.Sinh%2A>|Zwraca sinus hiperboliczny odpowiadający podanemu kątowi.|
|<xref:System.Math.Sqrt%2A>|Zwraca pierwiastek kwadratowy z podanej liczby.|
|<xref:System.Math.Tan%2A>|Zwraca tangens podanego kąta.|
|<xref:System.Math.Tanh%2A>|Zwraca tangens hiperboliczny odpowiadający podanemu kątowi.|
|<xref:System.Math.Truncate%2A>|Oblicza integralną część określonego `Decimal` lub `Double` numer.|

W poniższej tabeli wymieniono metody klasy <xref:System.Math?displayProperty=nameWithType>, które nie istnieją w .NET Framework, ale są dodawane w .NET Standard lub .NET Core:

|Metoda .NET|Opis|Dostępne w|
|---------------------------|-----------------|-----------|
|<xref:System.Math.Acosh%2A>|Zwraca kąt, którego cosinus hiperboliczny jest równy podanej liczbie.|Począwszy od platformy .NET Core 2,1 i .NET Standard 2,1|
|<xref:System.Math.Asinh%2A>|Zwraca kąt, którego sinus hiperboliczny jest podaną liczbą.|Począwszy od platformy .NET Core 2,1 i .NET Standard 2,1|
|<xref:System.Math.Atanh%2A>|Zwraca kąt, którego tangens hiperboliczny jest równy podanej liczbie.|Począwszy od platformy .NET Core 2,1 i .NET Standard 2,1|
|<xref:System.Math.BitDecrement%2A>|Zwraca następną najmniejszą wartość, która porównuje mniej niż `x`.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.BitIncrement%2A>|Zwraca następną największą wartość, która porównuje więcej niż `x`.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.Cbrt%2A>|Zwraca katalog główny modułu o podanej liczbie.|Począwszy od platformy .NET Core 2,1 i .NET Standard 2,1|
|<xref:System.Math.Clamp%2A>|Zwraca `value` zamocowany do zakresu z zakresem `min` i `max`.|Począwszy od platformy .NET Core 2,0 i .NET Standard 2,1|
|<xref:System.Math.CopySign%2A>|Zwraca wartość o wielkości `x` i znaku `y`.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.FusedMultiplyAdd%2A>|Zwraca (x \* y) + z, zaokrągloną jako jedną operację Trzyelementowy.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.ILogB%2A>|Zwraca logarytm dziesiętny z podanej liczby.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.Log2%2A>|Zwraca logarytm o podstawie 2 dla podanej liczby.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.MaxMagnitude%2A>|Zwraca większą liczbę liczb zmiennoprzecinkowych o podwójnej precyzji.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.MinMagnitude%2A>|Zwraca mniejszy rozmiar dwóch liczb zmiennoprzecinkowych podwójnej precyzji.|Począwszy od platformy .NET Core 3,0|
|<xref:System.Math.ScaleB%2A>|Zwraca wartość x \* 2 ^ n obliczona efektywnie.|Począwszy od platformy .NET Core 3,0|

Aby korzystać z tych funkcji bez kwalifikacji, zaimportuj <xref:System.Math?displayProperty=nameWithType> przestrzeni nazw do projektu, dodając następujący kod na początku pliku źródłowego:

```vb
Imports System.Math
```

## <a name="example---abs"></a>Przykład — ABS

W tym przykładzie zastosowano metodę <xref:System.Math.Abs%2A> klasy <xref:System.Math>, aby obliczyć wartość bezwzględną liczby.

```vb
Dim x As Double = Math.Abs(50.3)
Dim y As Double = Math.Abs(-50.3)
Console.WriteLine(x)
Console.WriteLine(y)
' This example produces the following output:
' 50.3
' 50.3
```  

## <a name="example---atan"></a>Przykład — atan

W tym przykładzie zastosowano metodę <xref:System.Math.Atan%2A> klasy <xref:System.Math>, aby obliczyć wartość pi.

```vb
Public Function GetPi() As Double
    ' Calculate the value of pi.
    Return 4.0 * Math.Atan(1.0)
End Function
```

> [!NOTE]
> Klasa <xref:System.Math?displayProperty=nameWithType> zawiera pole stałej <xref:System.Math.PI?displayProperty=nameWithType>. Można go użyć zamiast obliczenia.

## <a name="example---cos"></a>Przykład — cos

W tym przykładzie zastosowano metodę <xref:System.Math.Cos%2A> klasy <xref:System.Math>, aby zwrócić cosinus kąta.

```vb
Public Function Sec(angle As Double) As Double
    ' Calculate the secant of angle, in radians.
    Return 1.0 / Math.Cos(angle)
End Function
```

## <a name="example---exp"></a>Przykład — EXP

W tym przykładzie zastosowano metodę <xref:System.Math.Exp%2A> klasy <xref:System.Math>, aby zwrócić wartość e podniesioną do potęgi.

```vb
Public Function Sinh(angle As Double) As Double
    ' Calculate hyperbolic sine of an angle, in radians.
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0
End Function
```

## <a name="example---log"></a>Przykład — dziennik

W tym przykładzie zastosowano metodę <xref:System.Math.Log%2A> klasy <xref:System.Math> do zwrócenia logarytmu naturalnego liczby.

```vb
Public Function Asinh(value As Double) As Double
    ' Calculate inverse hyperbolic sine, in radians.
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))
End Function
```

## <a name="example---round"></a>Przykład — zaokrąglony

W tym przykładzie zastosowano metodę <xref:System.Math.Round%2A> klasy <xref:System.Math>, aby zaokrąglić liczbę do najbliższej liczby całkowitej.

```vb
Dim myVar2 As Double = Math.Round(2.8)
Console.WriteLine(myVar2)
' The code produces the following output:
' 3
```

## <a name="example---sign"></a>Przykład — znak

W tym przykładzie zastosowano metodę <xref:System.Math.Sign%2A> klasy <xref:System.Math>, aby określić znak liczby.

```vb
Dim mySign1 As Integer = Math.Sign(12)
Dim mySign2 As Integer = Math.Sign(-2.4)
Dim mySign3 As Integer = Math.Sign(0)
Console.WriteLine(mySign1)
Console.WriteLine(mySign2)
Console.WriteLine(mySign3)
' The code produces the following output:
' 1
' -1
' 0
```

## <a name="example---sin"></a>Przykład — Sin

W tym przykładzie zastosowano metodę <xref:System.Math.Sin%2A> klasy <xref:System.Math>, aby zwrócić sinus kąta.

```vb
Public Function Csc(angle As Double) As Double
    ' Calculate cosecant of an angle, in radians.
    Return 1.0 / Math.Sin(angle)
End Function
```

## <a name="example---sqrt"></a>Przykład — sqrt

W tym przykładzie zastosowano metodę <xref:System.Math.Sqrt%2A> klasy <xref:System.Math>, aby obliczyć pierwiastek kwadratowy liczby.

```vb
Dim mySqrt1 As Double = Math.Sqrt(4)
Dim mySqrt2 As Double = Math.Sqrt(23)
Dim mySqrt3 As Double = Math.Sqrt(0)
Dim mySqrt4 As Double = Math.Sqrt(-4)
Console.WriteLine(mySqrt1)
Console.WriteLine(mySqrt2)
Console.WriteLine(mySqrt3)
Console.WriteLine(mySqrt4)
' The code produces the following output:
' 2
' 4.79583152331272
' 0
' NaN
```

## <a name="example---tan"></a>Przykład — Tan

W tym przykładzie zastosowano metodę <xref:System.Math.Tan%2A> klasy <xref:System.Math>, aby zwrócić tangens kąta.

```vb
Public Function Ctan(angle As Double) As Double
    ' Calculate cotangent of an angle, in radians.
    Return 1.0 / Math.Tan(angle)
End Function
```

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Pochodne funkcje matematyczne](../keywords/derived-math-functions.md)
- [Operatory arytmetyczne](../operators/arithmetic-operators.md)
