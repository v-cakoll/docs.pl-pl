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
ms.openlocfilehash: 87faa623f5b145eec8b88e350fce4171125324dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596811"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="57916-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57916-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="57916-103">W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą być uzyskane z funkcji wewnętrznej matematyczne <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="57916-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="57916-104">Funkcje matematyczne wewnętrzne są dostępne przez dodanie `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="57916-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="57916-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="57916-105">Function</span></span>|<span data-ttu-id="57916-106">Odpowiedniki pochodne</span><span class="sxs-lookup"><span data-stu-id="57916-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="57916-107">Secans (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="57916-107">Secant (Sec(x))</span></span>|<span data-ttu-id="57916-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="57916-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="57916-109">Cosecans (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="57916-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="57916-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="57916-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="57916-111">Cotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="57916-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="57916-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="57916-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="57916-113">Odwrotny sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="57916-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="57916-114">ATAN (x / Sqrt (-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="57916-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="57916-115">Cosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="57916-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="57916-116">ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="57916-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="57916-117">Odwrotny secans (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="57916-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="57916-118">2 * Atan(1) — Atan(Sign(x) / Sqrt (x \* x-1))</span><span class="sxs-lookup"><span data-stu-id="57916-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="57916-119">Odwrotny cosecans (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="57916-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="57916-120">ATAN(sign(x) / Sqrt (x \* x 1))</span><span class="sxs-lookup"><span data-stu-id="57916-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="57916-121">Odwrotny cotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="57916-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="57916-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="57916-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="57916-123">Sinus hiperboliczny (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="57916-124">(Exp(x) — Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="57916-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="57916-125">Cosinus hiperboliczny (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="57916-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="57916-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="57916-127">Tangens hiperboliczny (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="57916-128">(Exp(x) — Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="57916-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="57916-129">Secans hiperboliczny (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="57916-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="57916-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="57916-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="57916-131">Cosecans hiperboliczny (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="57916-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="57916-132">2 / (Exp(x) — Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="57916-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="57916-133">Cotangens hiperboliczny (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="57916-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="57916-134">(Exp(x) + Exp(-x)) / (Exp(x) — Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="57916-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="57916-135">Odwrotny sinus hiperboliczny (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="57916-136">Dziennik (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="57916-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="57916-137">Odwrotny cosinus hiperboliczny (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="57916-138">Dziennik (x + Sqrt (x \* x 1))</span><span class="sxs-lookup"><span data-stu-id="57916-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="57916-139">Odwrotny tangens hiperboliczny (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="57916-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="57916-140">Dziennik ((1 + x) / (x 1 –)) / 2</span><span class="sxs-lookup"><span data-stu-id="57916-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="57916-141">Odwrotny secans hiperboliczny (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="57916-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="57916-142">Dziennik ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="57916-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="57916-143">Odwrotny cosecans hiperboliczny (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="57916-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="57916-144">Log((sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="57916-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="57916-145">Odwrotny cotangens hiperboliczny (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="57916-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="57916-146">Dziennik ((x + 1) / (x-1)) / 2</span><span class="sxs-lookup"><span data-stu-id="57916-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57916-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57916-147">See Also</span></span>  
 [<span data-ttu-id="57916-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="57916-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
