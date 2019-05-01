---
title: Pochodne funkcje matematyczne (Visual Basic)
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
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801897"
---
# <a name="derived-math-functions-visual-basic"></a>Pochodne funkcje matematyczne (Visual Basic)
W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą pochodzić z funkcji matematycznych wewnętrzne <xref:System.Math?displayProperty=nameWithType> obiektu. Dostęp do funkcji matematycznych wewnętrzne, dodając `Imports System.Math` do pliku lub projektu.  
  
|Funkcja|Odpowiedniki pochodne|  
|--------------|-------------------------|  
|Secans (Sec(x))|1 / Cos(x)|  
|Cosecans (Csc(x))|1 / Sin(x)|  
|Cotangens (Ctan(x))|1 / Tan(x)|  
|Arcus sinus (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|Arcus cosinus (Acos(x))|ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|Odwrotny secans (Asec(x))|2 * Atan(1) — Atan(Sign(x) / Sqrt (x \* x — 1))|  
|Odwrotny cosecans (Acsc(x))|Atan(Sign(x) / Sqrt(x * x – 1))|  
|Odwrotność wartości cotangens (Acot(x))|2 * Atan(1) - Atan(x)|  
|Sinus hiperboliczny (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Cosinus hiperboliczny (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Tangens hiperboliczny (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Secans hiperboliczny (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Cosecans hiperboliczny (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Cotangens hiperboliczny (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Sinus hiperboliczny (Asinh(x))|Dziennik (x + Sqrt (x * x + 1))|  
|Odwrotny cosinus hiperboliczny (Acosh(x))|Dziennik (x + Sqrt (x * x — 1))|  
|Arcus tangens hiperboliczny (Atanh(x))|Dziennik ((1 + x) / (1 – x)) / 2|  
|Odwrotny secans hiperboliczny (AsecH(x))|Dziennik ((Sqrt (-x * x + 1) + 1) / x)|  
|Odwrotny cosecans hiperboliczny (Acsch(x))|Log((sign(x) * Sqrt (x \* x + 1) + 1) / x)|  
|Odwrotny cotangens hiperboliczny (Acoth(x))|Dziennik ((x + 1) / (x — 1)) / 2|  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje matematyczne](../../../visual-basic/language-reference/functions/math-functions.md)
