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
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="b066f-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b066f-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="b066f-103">W poniższej tabeli przedstawiono funkcje matematyczne inne niż wewnętrzne, które mogą pochodzić z wewnętrznych funkcji matematycznych <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b066f-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="b066f-104">Możesz uzyskać dostęp do wewnętrznych funkcji matematycznych przez dodanie `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="b066f-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="b066f-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="b066f-105">Function</span></span>|<span data-ttu-id="b066f-106">Pochodne równoważne</span><span class="sxs-lookup"><span data-stu-id="b066f-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="b066f-107">Secans (sek. x))</span><span class="sxs-lookup"><span data-stu-id="b066f-107">Secant (Sec(x))</span></span>|<span data-ttu-id="b066f-108">1/cos (x)</span><span class="sxs-lookup"><span data-stu-id="b066f-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="b066f-109">Cosecans (CSC (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="b066f-110">1/Sin (x)</span><span class="sxs-lookup"><span data-stu-id="b066f-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="b066f-111">Cotangens (CTAN (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="b066f-112">1/Tan (x)</span><span class="sxs-lookup"><span data-stu-id="b066f-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="b066f-113">Arcus sinus (ASIN (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="b066f-114">ATAN (x/sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="b066f-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="b066f-115">Arcus cosinus (Acos (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="b066f-116">ATAN (-x/sqrt (-x \* x + 1))) + 2 \* ATAN (1)</span><span class="sxs-lookup"><span data-stu-id="b066f-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="b066f-117">Odwrotny secans (ASEC (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="b066f-118">2 \* ATAN (1) — ATAN (Sign (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b066f-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b066f-119">Odwrotny cosecans (ACSC (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="b066f-120">ATAN (Sign (x)/SQRT (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b066f-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b066f-121">Cotangens odwrotny (ACOT (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="b066f-122">2 \* ATAN (1) — ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="b066f-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="b066f-123">Sinus hiperboliczny (sinh (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="b066f-124">(EXP (x) – EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="b066f-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="b066f-125">Cosinus hiperboliczny (COSH — (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="b066f-126">(EXP (x) + EXP (-x))/2</span><span class="sxs-lookup"><span data-stu-id="b066f-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="b066f-127">Tangens hiperboliczny (tanh (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="b066f-128">(EXP (x) – EXP (-x))/(EXP (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="b066f-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="b066f-129">Secans hiperboliczny (sech (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="b066f-130">2/(EXP (x) + EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="b066f-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="b066f-131">Cosecans hiperboliczny (csch (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="b066f-132">2/(EXP (x) — EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="b066f-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="b066f-133">Cotangens hiperboliczny (coth (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="b066f-134">(EXP (x) + EXP (-x))/(EXP (x) – EXP (-x))</span><span class="sxs-lookup"><span data-stu-id="b066f-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="b066f-135">Arcus sinus hiperboliczny (ASINH — (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="b066f-136">Dziennik (x + sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="b066f-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="b066f-137">Arcus cosinus hiperboliczny (ACOSH — (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="b066f-138">Dziennik (x + sqrt (x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="b066f-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="b066f-139">Odwrotny tangens hiperboliczny (ATANH — (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="b066f-140">Dziennik ((1 + x)/(1 – x))/2</span><span class="sxs-lookup"><span data-stu-id="b066f-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="b066f-141">Odwrotny secans hiperboliczny (AsecH (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="b066f-142">Dziennik ((sqrt (-x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="b066f-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="b066f-143">Odwrotny cosecans hiperboliczny (acsch (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="b066f-144">Log (znak (x) \* SQRT (x \* x + 1) + 1)/x)</span><span class="sxs-lookup"><span data-stu-id="b066f-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="b066f-145">Odwrotny cotangens hiperboliczny (ACOTH (x))</span><span class="sxs-lookup"><span data-stu-id="b066f-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="b066f-146">Dziennik ((x + 1)/(x – 1))/2</span><span class="sxs-lookup"><span data-stu-id="b066f-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b066f-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b066f-147">See also</span></span>

- [<span data-ttu-id="b066f-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="b066f-148">Math Functions</span></span>](../functions/math-functions.md)
