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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836587"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="553d7-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="553d7-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="553d7-103">W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą pochodzić z funkcji matematycznych wewnętrzne <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="553d7-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="553d7-104">Dostęp do funkcji matematycznych wewnętrzne, dodając `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="553d7-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="553d7-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="553d7-105">Function</span></span>|<span data-ttu-id="553d7-106">Odpowiedniki pochodne</span><span class="sxs-lookup"><span data-stu-id="553d7-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="553d7-107">Secans (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-107">Secant (Sec(x))</span></span>|<span data-ttu-id="553d7-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="553d7-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="553d7-109">Cosecans (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="553d7-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="553d7-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="553d7-111">Cotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="553d7-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="553d7-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="553d7-113">Arcus sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="553d7-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="553d7-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="553d7-115">Arcus cosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="553d7-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="553d7-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="553d7-117">Odwrotny secans (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="553d7-118">2 \* Atan(1) — Atan(Sign(x) / Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="553d7-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="553d7-119">Odwrotny cosecans (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="553d7-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="553d7-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="553d7-121">Odwrotność wartości cotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="553d7-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="553d7-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="553d7-123">Sinus hiperboliczny (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="553d7-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="553d7-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="553d7-125">Cosinus hiperboliczny (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="553d7-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="553d7-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="553d7-127">Tangens hiperboliczny (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="553d7-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="553d7-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="553d7-129">Secans hiperboliczny (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="553d7-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="553d7-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="553d7-131">Cosecans hiperboliczny (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="553d7-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="553d7-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="553d7-133">Cotangens hiperboliczny (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="553d7-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="553d7-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="553d7-135">Sinus hiperboliczny (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="553d7-136">Dziennik (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="553d7-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="553d7-137">Odwrotny cosinus hiperboliczny (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="553d7-138">Dziennik (x + Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="553d7-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="553d7-139">Arcus tangens hiperboliczny (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="553d7-140">Dziennik ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="553d7-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="553d7-141">Odwrotny secans hiperboliczny (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="553d7-142">Dziennik ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="553d7-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="553d7-143">Odwrotny cosecans hiperboliczny (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="553d7-144">Log((sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="553d7-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="553d7-145">Odwrotny cotangens hiperboliczny (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="553d7-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="553d7-146">Dziennik ((x + 1) / (x — 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="553d7-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="553d7-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="553d7-147">See also</span></span>

- [<span data-ttu-id="553d7-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="553d7-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
