---
title: Funkcje matematyczne
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: b1cd6a846a7dc1dddcf6bdb5eb99ebc1c57a012c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348062"
---
# <a name="math-functions-visual-basic"></a>Funkcje matematyczne (Visual Basic)
Metody klasy <xref:System.Math?displayProperty=nameWithType> zapewniają trygonometryczne, logarytmiczne i inne typowe funkcje matematyczne.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono metody klasy <xref:System.Math?displayProperty=nameWithType>. Można ich używać w programie Visual Basic.  
  
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
  
 Aby korzystać z tych funkcji bez kwalifikacji, zaimportuj <xref:System.Math?displayProperty=nameWithType> przestrzeni nazw do projektu, dodając następujący kod na początku pliku źródłowego:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Abs%2A> klasy <xref:System.Math>, aby obliczyć wartość bezwzględną liczby.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Atan%2A> klasy <xref:System.Math>, aby obliczyć wartość pi.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Cos%2A> klasy <xref:System.Math>, aby zwrócić cosinus kąta.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Exp%2A> klasy <xref:System.Math>, aby zwrócić wartość e podniesioną do potęgi.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Log%2A> klasy <xref:System.Math> do zwrócenia logarytmu naturalnego liczby.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Round%2A> klasy <xref:System.Math>, aby zaokrąglić liczbę do najbliższej liczby całkowitej.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Sign%2A> klasy <xref:System.Math>, aby określić znak liczby.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Sin%2A> klasy <xref:System.Math>, aby zwrócić sinus kąta.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Sqrt%2A> klasy <xref:System.Math>, aby obliczyć pierwiastek kwadratowy liczby.  
  
```vb
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zastosowano metodę <xref:System.Math.Tan%2A> klasy <xref:System.Math>, aby zwrócić tangens kąta.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Wymagania  
 **Klasa:** <xref:System.Math>  
  
 **Przestrzeń nazw:** <xref:System>  
  
 **Zestaw:** mscorlib (w bibliotece Mscorlib. dll)  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [Pochodne funkcje matematyczne](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
