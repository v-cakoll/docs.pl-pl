---
title: Funkcje matematyczne (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d67df44e5f4ea89475ea34e87fd5041ee6cb44f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="math-functions-visual-basic"></a>Funkcje matematyczne (Visual Basic)
Metody <xref:System.Math?displayProperty=nameWithType> klasy Podaj trygonometryczne logarytmicznej i inne typowe funkcje matematyczne.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono metody <xref:System.Math?displayProperty=nameWithType> klasy. Umożliwiają one w programie Visual Basic.  
  
|.NET framework — metoda|Opis|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Zwraca wartość bezwzględną liczby.|  
|<xref:System.Math.Acos%2A>|Zwraca kąt, którego cosinus jest równy podanej liczbie.|  
|<xref:System.Math.Asin%2A>|Zwraca kąt, którego sinus jest równy podanej liczbie.|  
|<xref:System.Math.Atan%2A>|Zwraca kąt, którego tangens jest równy podanej liczbie.|  
|<xref:System.Math.Atan2%2A>|Zwraca kąt, którego tangens jest równy ilorazowi dwóch podanych liczb.|  
|<xref:System.Math.BigMul%2A>|Zwraca pełny iloczyn dwóch liczb 32-bitowych.|  
|<xref:System.Math.Ceiling%2A>|Zwraca najmniejszą wartość całkowitą, która jest większa niż lub równa określonej `Decimal` lub `Double`.|  
|<xref:System.Math.Cos%2A>|Zwraca cosinus odpowiadający podanemu kątowi.|  
|<xref:System.Math.Cosh%2A>|Zwraca cosinus hiperboliczny podanemu kątowi.|  
|<xref:System.Math.DivRem%2A>|Zwraca iloraz dwóch 32-bitowy lub 64-bitowych liczb całkowitych ze znakiem, a także zwraca resztę do parametru output.|  
|<xref:System.Math.Exp%2A>|Zwraca wartość liczby e (podstawę logarytmów naturalnych) podniesione do określonej potęgi.|  
|<xref:System.Math.Floor%2A>|Zwraca największa liczba całkowita, która jest mniejsza lub równa do określonego `Decimal` lub `Double` numer.|  
|<xref:System.Math.IEEERemainder%2A>|Zwraca resztę będącą wynikiem podziału określonym przez inny określić numer.|  
|<xref:System.Math.Log%2A>|Zwraca logarytm naturalny (o podstawie e) podanej liczby lub logarytmu określonej liczby w określonej podstawy.|  
|<xref:System.Math.Log10%2A>|Zwraca logarytm 10 podanej liczby.|  
|<xref:System.Math.Max%2A>|Zwraca większych dwóch liczb.|  
|<xref:System.Math.Min%2A>|Zwraca mniejszy z dwóch liczb.|  
|<xref:System.Math.Pow%2A>|Zwraca określoną liczbę podniesioną do wskazanej potęgi.|  
|<xref:System.Math.Round%2A>|Zwraca `Decimal` lub `Double` wartość zaokrąglona do najbliższej wartości całkowitych lub do określonej liczby cyfr ułamkowych.|  
|<xref:System.Math.Sign%2A>|Zwraca `Integer` wartość określającą znak liczby.|  
|<xref:System.Math.Sin%2A>|Zwraca sinus określonego kąta.|  
|<xref:System.Math.Sinh%2A>|Zwraca sinus hiperboliczny podanemu kątowi.|  
|<xref:System.Math.Sqrt%2A>|Zwraca pierwiastek kwadratowy z podanej liczby.|  
|<xref:System.Math.Tan%2A>|Zwraca tangens odpowiadający podanemu kątowi.|  
|<xref:System.Math.Tanh%2A>|Zwraca tangens hiperboliczny podanemu kątowi.|  
|<xref:System.Math.Truncate%2A>|Oblicza integralną częścią określonej `Decimal` lub `Double` numer.|  
  
 Aby korzystać z tych funkcji bez kwalifikacji, należy zaimportować <xref:System.Math?displayProperty=nameWithType> przestrzeni nazw do projektu, dodając następujący kod na początku pliku źródłowego:  
  
```  
Imports System.Math  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Abs%2A> metody <xref:System.Math> klasę, aby obliczyć wartość bezwzględną liczby.  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Atan%2A> metody <xref:System.Math> klasę, aby obliczyć wartość liczby pi.  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Cos%2A> metody <xref:System.Math> klasy, która zwraca cosinus kąta.  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Exp%2A> metody <xref:System.Math> służącą do zwracania liczby e podniesionej do potęgi.  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Log%2A> metody <xref:System.Math> klasy Zwraca logarytm naturalny liczby.  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Round%2A> metody <xref:System.Math> klasy zostać zaokrąglona liczba do najbliższej liczby całkowitej.  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sign%2A> metody <xref:System.Math> klasę, aby określić znak liczby.  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sin%2A> metody <xref:System.Math> służącą do zwracania sinus kąta.  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Math.Sqrt%2A> metody <xref:System.Math> klasę, aby obliczyć pierwiastek kwadratowy z liczby.  
  
```  
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
 W tym przykładzie użyto <xref:System.Math.Tan%2A> metody <xref:System.Math> służącą do zwracania tangens kąta.  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>Wymagania  
 **Klasa:**<xref:System.Math>  
  
 **Namespace:**<xref:System>  
  
 **Zestaw:** mscorlib (w bibliotece mscorlib.dll)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>  
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>  
 <xref:System.Double.NaN>  
 [Pochodne funkcje matematyczne](../../../visual-basic/language-reference/keywords/derived-math-functions.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
