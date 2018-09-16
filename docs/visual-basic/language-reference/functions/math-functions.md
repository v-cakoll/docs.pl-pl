---
title: Funkcje matematyczne (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: da0b612feb5b9a479d50f52cf65e38007ab3b196
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675720"
---
# <a name="math-functions-visual-basic"></a>Funkcje matematyczne (Visual Basic)
Metody <xref:System.Math?displayProperty=nameWithType> klasy dostarczają trygonometrycznych logarytmicznej i inne typowe funkcje matematyczne.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli wymieniono metody <xref:System.Math?displayProperty=nameWithType> klasy. Można ich użyć w programie Visual Basic.  
  
|.NET — metoda|Opis|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Zwraca wartość bezwzględną liczby.|  
|<xref:System.Math.Acos%2A>|Zwraca kąt, którego cosinus jest równy podanej liczbie.|  
|<xref:System.Math.Asin%2A>|Zwraca kąt, którego sinus jest równy podanej liczbie.|  
|<xref:System.Math.Atan%2A>|Zwraca kąt, którego tangens jest równy podanej liczbie.|  
|<xref:System.Math.Atan2%2A>|Zwraca kąt, którego tangens jest równy ilorazowi dwóch podanych liczb.|  
|<xref:System.Math.BigMul%2A>|Zwraca pełny iloczyn dwóch liczb 32-bitowych.|  
|<xref:System.Math.Ceiling%2A>|Zwraca najmniejszą wartość całkowita, która jest większa lub równa określonej `Decimal` lub `Double`.|  
|<xref:System.Math.Cos%2A>|Zwraca cosinus określonego kąta.|  
|<xref:System.Math.Cosh%2A>|Zwraca cosinus hiperboliczny podanemu kątowi.|  
|<xref:System.Math.DivRem%2A>|Zwraca iloraz dwóch 32-bitową lub 64-bitowych oznaczone liczby całkowite, a także zwraca resztę z dzielenia parametr danych wyjściowych.|  
|<xref:System.Math.Exp%2A>|Zwraca wartość liczby e (base logarytmy naturalne) podniesione do określonej potęgi.|  
|<xref:System.Math.Floor%2A>|Zwraca największą liczbą całkowitą, która jest mniejsza lub równa określonej `Decimal` lub `Double` numer.|  
|<xref:System.Math.IEEERemainder%2A>|Zwraca resztę, która wynika z podziału określoną liczbę przez inny określony numer.|  
|<xref:System.Math.Log%2A>|Zwraca logarytm naturalny (o podstawie e) podanej liczby lub logarytmu określonej liczby w określonej podstawie.|  
|<xref:System.Math.Log10%2A>|Zwraca logarytm 10 określoną liczbę.|  
|<xref:System.Math.Max%2A>|Zwraca większy z dwóch liczb.|  
|<xref:System.Math.Min%2A>|Zwraca wartość mniejszą z dwóch liczb.|  
|<xref:System.Math.Pow%2A>|Zwraca określoną liczbę podniesioną do wskazanej potęgi.|  
|<xref:System.Math.Round%2A>|Zwraca `Decimal` lub `Double` wartość jest zaokrąglana do najbliższej wartości całkowitej lub określonej liczby cyfr dziesiętnych.|  
|<xref:System.Math.Sign%2A>|Zwraca `Integer` wartość określającą znak liczby.|  
|<xref:System.Math.Sin%2A>|Zwraca sinus określonego kąta.|  
|<xref:System.Math.Sinh%2A>|Zwraca sinus hiperboliczny liczby podanemu kątowi.|  
|<xref:System.Math.Sqrt%2A>|Zwraca pierwiastek kwadratowy z podanej liczby.|  
|<xref:System.Math.Tan%2A>|Zwraca tangens określonego kąta.|  
|<xref:System.Math.Tanh%2A>|Zwraca tangens hiperboliczny podanemu kątowi.|  
|<xref:System.Math.Truncate%2A>|Oblicza integralną częścią określonego `Decimal` lub `Double` numer.|  
  
 Aby korzystać z tych funkcji bez kwalifikacji, należy zaimportować <xref:System.Math?displayProperty=nameWithType> przestrzeni nazw do projektu, dodając następujący kod na początku pliku źródłowego:  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Abs%2A> metody <xref:System.Math> klasy, aby obliczyć wartość bezwzględną liczby.  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Atan%2A> metody <xref:System.Math> klasy, aby obliczyć wartość liczby pi.  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Cos%2A> metody <xref:System.Math> klasy w celu zwracania cosinus kąta.  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Exp%2A> metody <xref:System.Math> klasy w celu zwracania liczby e podniesionej do potęgi.  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Log%2A> metody <xref:System.Math> klasy w celu zwracania logarytm naturalny liczby.  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Round%2A> metody <xref:System.Math> klasy zaokrąglają liczbę do najbliższej liczby całkowitej.  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sign%2A> metody <xref:System.Math> klasę, aby określić znak liczby.  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sin%2A> metody <xref:System.Math> klasy w celu zwracania sinus kąta.  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sqrt%2A> metody <xref:System.Math> klasy, aby obliczyć pierwiastek kwadratowy liczby.  
  
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
 W tym przykładzie użyto <xref:System.Math.Tan%2A> metody <xref:System.Math> klasy w celu zwracania tangens kąta.  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Wymagania  
 **Klasa:** <xref:System.Math>  
  
 **Namespace:** <xref:System>  
  
 **Zestaw:** mscorlib (w mscorlib.dll)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [Pochodne funkcje matematyczne](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
