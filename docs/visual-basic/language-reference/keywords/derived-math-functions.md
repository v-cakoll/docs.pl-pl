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
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836587"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="15fdc-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15fdc-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="15fdc-103">W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą pochodzić z funkcji matematycznych wewnętrzne <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="15fdc-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="15fdc-104">Dostęp do funkcji matematycznych wewnętrzne, dodając `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="15fdc-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="15fdc-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="15fdc-105">Function</span></span>|<span data-ttu-id="15fdc-106">Odpowiedniki pochodne</span><span class="sxs-lookup"><span data-stu-id="15fdc-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="15fdc-107">Secans (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-107">Secant (Sec(x))</span></span>|<span data-ttu-id="15fdc-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="15fdc-109">Cosecans (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="15fdc-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="15fdc-111">Cotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="15fdc-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="15fdc-113">Arcus sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="15fdc-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="15fdc-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="15fdc-115">Arcus cosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="15fdc-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="15fdc-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="15fdc-117">Odwrotny secans (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="15fdc-118">2 \* Atan(1) — Atan(Sign(x) / Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="15fdc-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="15fdc-119">Odwrotny cosecans (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="15fdc-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="15fdc-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="15fdc-121">Odwrotność wartości cotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="15fdc-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="15fdc-123">Sinus hiperboliczny (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="15fdc-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="15fdc-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="15fdc-125">Cosinus hiperboliczny (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="15fdc-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="15fdc-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="15fdc-127">Tangens hiperboliczny (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="15fdc-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="15fdc-129">Secans hiperboliczny (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="15fdc-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="15fdc-131">Cosecans hiperboliczny (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="15fdc-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="15fdc-133">Cotangens hiperboliczny (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="15fdc-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="15fdc-135">Sinus hiperboliczny (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="15fdc-136">Dziennik (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="15fdc-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="15fdc-137">Odwrotny cosinus hiperboliczny (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="15fdc-138">Dziennik (x + Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="15fdc-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="15fdc-139">Arcus tangens hiperboliczny (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="15fdc-140">Dziennik ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="15fdc-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="15fdc-141">Odwrotny secans hiperboliczny (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="15fdc-142">Dziennik ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="15fdc-143">Odwrotny cosecans hiperboliczny (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="15fdc-144">Log((sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="15fdc-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="15fdc-145">Odwrotny cotangens hiperboliczny (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="15fdc-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="15fdc-146">Dziennik ((x + 1) / (x — 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="15fdc-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15fdc-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15fdc-147">See also</span></span>

- [<span data-ttu-id="15fdc-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="15fdc-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
