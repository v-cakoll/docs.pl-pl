---
title: Pochodne funkcje matematyczne
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 611f3d8faf2148b8a983467d9ace4fd6c18b30e6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373895"
---
# <a name="derived-math-functions-visual-basic"></a>Pochodne funkcje matematyczne (Visual Basic)
W poniższej tabeli przedstawiono funkcje matematyczne inne niż wewnętrzne, które mogą pochodzić z wewnętrznych funkcji matematycznych <xref:System.Math?displayProperty=nameWithType> obiektu. Możesz uzyskać dostęp do wewnętrznych funkcji matematycznych przez dodanie `Imports System.Math` do pliku lub projektu.  
  
|Funkcja|Pochodne równoważne|  
|--------------|-------------------------|  
|Secans (sek. x))|1/cos (x)|  
|Cosecans (CSC (x))|1/Sin (x)|  
|Cotangens (CTAN (x))|1/Tan (x)|  
|Arcus sinus (ASIN (x))|ATAN (x/sqrt (-x * x + 1))|  
|Arcus cosinus (Acos (x))|ATAN (-x/sqrt (-x * x + 1))) + 2 \* ATAN (1)|  
|Odwrotny secans (ASEC (x))|2 * ATAN (1) — ATAN (Sign (x)/SQRT (x \* x – 1))|  
|Odwrotny cosecans (ACSC (x))|ATAN (Sign (x)/SQRT (x * x – 1))|  
|Cotangens odwrotny (ACOT (x))|2 * ATAN (1) — ATAN (x)|  
|Sinus hiperboliczny (sinh (x))|(EXP (x) – EXP (-x))/2|  
|Cosinus hiperboliczny (COSH — (x))|(EXP (x) + EXP (-x))/2|  
|Tangens hiperboliczny (tanh (x))|(EXP (x) – EXP (-x))/(EXP (x) + EXP (-x))|  
|Secans hiperboliczny (sech (x))|2/(EXP (x) + EXP (-x))|  
|Cosecans hiperboliczny (csch (x))|2/(EXP (x) — EXP (-x))|  
|Cotangens hiperboliczny (coth (x))|(EXP (x) + EXP (-x))/(EXP (x) – EXP (-x))|  
|Arcus sinus hiperboliczny (ASINH — (x))|Dziennik (x + sqrt (x * x + 1))|  
|Arcus cosinus hiperboliczny (ACOSH — (x))|Dziennik (x + sqrt (x * x – 1))|  
|Odwrotny tangens hiperboliczny (ATANH — (x))|Dziennik ((1 + x)/(1 – x))/2|  
|Odwrotny secans hiperboliczny (AsecH (x))|Dziennik ((sqrt (-x * x + 1) + 1)/x)|  
|Odwrotny cosecans hiperboliczny (acsch (x))|Log (znak (x) * SQRT (x \* x + 1) + 1)/x)|  
|Odwrotny cotangens hiperboliczny (ACOTH (x))|Dziennik ((x + 1)/(x – 1))/2|  
  
## <a name="see-also"></a>Zobacz też

- [Funkcje matematyczne](../functions/math-functions.md)
