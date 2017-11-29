---
title: Pochodne funkcje matematyczne (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="636ad-102">Pochodne funkcje matematyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="636ad-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="636ad-103">W poniższej tabeli przedstawiono funkcje matematyczne — wewnętrzne, które mogą być uzyskane z funkcji wewnętrznej matematyczne <xref:System.Math?displayProperty=nameWithType> obiektu.</span><span class="sxs-lookup"><span data-stu-id="636ad-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="636ad-104">Funkcje matematyczne wewnętrzne są dostępne przez dodanie `Imports System.Math` do pliku lub projektu.</span><span class="sxs-lookup"><span data-stu-id="636ad-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="636ad-105">Funkcja</span><span class="sxs-lookup"><span data-stu-id="636ad-105">Function</span></span>|<span data-ttu-id="636ad-106">Odpowiedniki pochodne</span><span class="sxs-lookup"><span data-stu-id="636ad-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="636ad-107">Secans (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-107">Secant (Sec(x))</span></span>|<span data-ttu-id="636ad-108">1 / Cos(x)</span><span class="sxs-lookup"><span data-stu-id="636ad-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="636ad-109">Cosecans (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="636ad-110">1 / Sin(x)</span><span class="sxs-lookup"><span data-stu-id="636ad-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="636ad-111">Cotangens (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="636ad-112">1 / Tan(x)</span><span class="sxs-lookup"><span data-stu-id="636ad-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="636ad-113">Odwrotny sinus (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="636ad-114">ATAN (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="636ad-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="636ad-115">Cosinus (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="636ad-116">ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="636ad-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="636ad-117">Odwrotny secans (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="636ad-118">2 * Atan(1) — Atan(Sign(x) / Sqrt (x \* x-1))</span><span class="sxs-lookup"><span data-stu-id="636ad-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="636ad-119">Odwrotny cosecans (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="636ad-120">ATAN(sign(x) / Sqrt (x * x 1))</span><span class="sxs-lookup"><span data-stu-id="636ad-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="636ad-121">Odwrotny cotangens (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="636ad-122">2 * Atan(1) - Atan(x)</span><span class="sxs-lookup"><span data-stu-id="636ad-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="636ad-123">Sinus hiperboliczny (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="636ad-124">(Exp(x) — Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="636ad-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="636ad-125">Cosinus hiperboliczny (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="636ad-126">(Exp(x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="636ad-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="636ad-127">Tangens hiperboliczny (Tanh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="636ad-128">(Exp(x) — Exp(-x)) / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="636ad-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="636ad-129">Secans hiperboliczny (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="636ad-130">2 / (Exp(x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="636ad-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="636ad-131">Cosecans hiperboliczny (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="636ad-132">2 / (Exp(x) — Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="636ad-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="636ad-133">Cotangens hiperboliczny (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="636ad-134">(Exp(x) + Exp(-x)) / (Exp(x) — Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="636ad-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="636ad-135">Odwrotny sinus hiperboliczny (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="636ad-136">Dziennik (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="636ad-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="636ad-137">Odwrotny cosinus hiperboliczny (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="636ad-138">Dziennik (x + Sqrt (x * x 1))</span><span class="sxs-lookup"><span data-stu-id="636ad-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="636ad-139">Odwrotny tangens hiperboliczny (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="636ad-140">Dziennik ((1 + x) / (x 1 –)) / 2</span><span class="sxs-lookup"><span data-stu-id="636ad-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="636ad-141">Odwrotny secans hiperboliczny (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="636ad-142">Dziennik ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="636ad-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="636ad-143">Odwrotny cosecans hiperboliczny (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="636ad-144">Log((sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="636ad-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="636ad-145">Odwrotny cotangens hiperboliczny (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="636ad-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="636ad-146">Dziennik ((x + 1) / (x-1)) / 2</span><span class="sxs-lookup"><span data-stu-id="636ad-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="636ad-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="636ad-147">See Also</span></span>  
 [<span data-ttu-id="636ad-148">Funkcje matematyczne</span><span class="sxs-lookup"><span data-stu-id="636ad-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
