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
ms.openlocfilehash: 1273871faf65afdd1a894c03f13a2c93507c1b13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505864"
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="99cb9-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99cb9-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="99cb9-103">W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą pochodzić z funkcji matematycznych wewnętrzne <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="99cb9-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="99cb9-104">Dostęp do funkcji matematycznych wewnętrzne, dodając `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="99cb9-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="99cb9-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="99cb9-105">Function</span></span>|<span data-ttu-id="99cb9-106">Odpowiedniki pochodne</span><span class="sxs-lookup"><span data-stu-id="99cb9-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="99cb9-107">Secans (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-107">Secant (Sec(x))</span></span>|<span data-ttu-id="99cb9-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="99cb9-109">Cosecans (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="99cb9-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="99cb9-111">Cotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="99cb9-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="99cb9-113">Arcus sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="99cb9-114">Atan(x / Sqrt(-x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="99cb9-114">Atan(x / Sqrt(-x \* x + 1))</span></span>|  
|<span data-ttu-id="99cb9-115">Arcus cosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="99cb9-116">ATAN (-x / Sqrt (-x \* x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="99cb9-116">Atan(-x / Sqrt(-x \* x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="99cb9-117">Odwrotny secans (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="99cb9-118">2 \* Atan(1) — Atan(Sign(x) / Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="99cb9-118">2 \* Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="99cb9-119">Odwrotny cosecans (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="99cb9-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span><span class="sxs-lookup"><span data-stu-id="99cb9-120">Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="99cb9-121">Odwrotność wartości cotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="99cb9-122">2 \* Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-122">2 \* Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="99cb9-123">Sinus hiperboliczny (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="99cb9-124">(Exp(x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="99cb9-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="99cb9-125">Cosinus hiperboliczny (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="99cb9-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="99cb9-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="99cb9-127">Tangens hiperboliczny (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="99cb9-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="99cb9-129">Secans hiperboliczny (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="99cb9-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="99cb9-131">Cosecans hiperboliczny (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="99cb9-132">2 / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="99cb9-133">Cotangens hiperboliczny (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="99cb9-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="99cb9-135">Sinus hiperboliczny (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="99cb9-136">Dziennik (x + Sqrt (x \* x + 1))</span><span class="sxs-lookup"><span data-stu-id="99cb9-136">Log(x + Sqrt(x \* x + 1))</span></span>|  
|<span data-ttu-id="99cb9-137">Odwrotny cosinus hiperboliczny (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="99cb9-138">Dziennik (x + Sqrt (x \* x — 1))</span><span class="sxs-lookup"><span data-stu-id="99cb9-138">Log(x + Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="99cb9-139">Arcus tangens hiperboliczny (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="99cb9-140">Dziennik ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="99cb9-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="99cb9-141">Odwrotny secans hiperboliczny (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="99cb9-142">Dziennik ((Sqrt (-x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-142">Log((Sqrt(-x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="99cb9-143">Odwrotny cosecans hiperboliczny (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="99cb9-144">Log((sign(x) \* Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="99cb9-144">Log((Sign(x) \* Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="99cb9-145">Odwrotny cotangens hiperboliczny (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="99cb9-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="99cb9-146">Dziennik ((x + 1) / (x — 1)) / 2</span><span class="sxs-lookup"><span data-stu-id="99cb9-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99cb9-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99cb9-147">See also</span></span>
- [<span data-ttu-id="99cb9-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="99cb9-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
