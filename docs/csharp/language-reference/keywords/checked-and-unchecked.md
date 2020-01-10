---
title: Zaznaczone i niezaznaczone — C# odwołanie
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a3b1ef8e6d8e496eda74ab25b3fe17f8174bac11
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713715"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="125ef-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="125ef-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="125ef-103">C#instrukcje mogą być wykonywane w kontekście zaznaczonym lub niezaznaczonym.</span><span class="sxs-lookup"><span data-stu-id="125ef-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="125ef-104">W kontekście, przepełnienie arytmetyczne wywołuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="125ef-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="125ef-105">W kontekście niesprawdzonym przepełnienie arytmetyczne jest ignorowane, a wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="125ef-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="125ef-106">[zaznaczone](checked.md) Określ sprawdzony kontekst.</span><span class="sxs-lookup"><span data-stu-id="125ef-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="125ef-107">[niezaznaczone](unchecked.md) Określ kontekst niesprawdzony.</span><span class="sxs-lookup"><span data-stu-id="125ef-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="125ef-108">Sprawdzanie przepełnienia ma wpływ na następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="125ef-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="125ef-109">Wyrażenia wykorzystujące następujące wstępnie zdefiniowane operatory w typach całkowitych:</span><span class="sxs-lookup"><span data-stu-id="125ef-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="125ef-110">`++`, `--`, `-`jednoargumentowy, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="125ef-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="125ef-111">Jawne konwersje liczbowe między typami całkowitymi lub z `float` lub `double` do typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="125ef-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="125ef-112">Jeśli nie `checked` ani `unchecked` jest określony, domyślny kontekst dla wyrażeń niestałych (wyrażenia, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość opcji kompilatora [-Checked](../compiler-options/checked-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="125ef-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="125ef-113">Domyślnie wartość tej opcji to unoptional, a operacje arytmetyczne są wykonywane w niesprawdzonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="125ef-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="125ef-114">W przypadku wyrażeń stałych (wyrażenia, które mogą być w pełni oceniane w czasie kompilacji), domyślnym kontekstem jest zawsze zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="125ef-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="125ef-115">Jeśli wyrażenie stałe nie jest jawnie umieszczane w niesprawdzonym kontekście, przepełnienie następuje podczas obliczania czasu kompilacji wyrażenia powodującego błędy czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="125ef-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="125ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="125ef-116">See also</span></span>

- [<span data-ttu-id="125ef-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="125ef-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="125ef-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="125ef-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="125ef-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="125ef-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="125ef-120">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="125ef-120">Statement Keywords</span></span>](statement-keywords.md)
