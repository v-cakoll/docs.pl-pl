---
title: Zaznaczone i niezaznaczone — odwołanie do języka C#
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 8ee4c481a30dce30029fbe8cc26f4798b523a7ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173643"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="be79c-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="be79c-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="be79c-103">Instrukcje C# można wykonać w kontekście zaznaczone lub niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="be79c-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="be79c-104">W kontekście sprawdzonym przepełnienie arytmetyczne wywołuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="be79c-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="be79c-105">W niezaznaczonym kontekście przepełnienie arytmetyczne jest ignorowane, a wynik jest obcinany przez odrzucenie wszystkich bitów wysokiego rzędu, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="be79c-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="be79c-106">[zaznaczone](checked.md) Określ zaznaczony kontekst.</span><span class="sxs-lookup"><span data-stu-id="be79c-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="be79c-107">[niezaznaczone](unchecked.md) Określ niezaznaczony kontekst.</span><span class="sxs-lookup"><span data-stu-id="be79c-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="be79c-108">Sprawdzanie przepełnienia ma wpływ na następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="be79c-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="be79c-109">Wyrażenia używające następujących wstępnie zdefiniowanych operatorów typów całek:</span><span class="sxs-lookup"><span data-stu-id="be79c-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="be79c-110">`++`, `--`, `-`bezzasadne `+`, `-` `*``/`</span><span class="sxs-lookup"><span data-stu-id="be79c-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="be79c-111">Jawne konwersje liczbowe między `float` `double` typami całki lub z lub do typu integralnego.</span><span class="sxs-lookup"><span data-stu-id="be79c-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="be79c-112">Jeśli nie `checked` `unchecked` określono ani nie określono, domyślny kontekst dla wyrażeń niestałych (wyrażeń, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość opcji kompilatora [zaznaczonego.](../compiler-options/checked-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="be79c-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="be79c-113">Domyślnie wartość tej opcji jest nieustawiona, a operacje arytmetyczne są wykonywane w niezaznaczonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="be79c-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>

 <span data-ttu-id="be79c-114">Dla wyrażeń stałych (wyrażeń, które mogą być w pełni oceniane w czasie kompilacji), kontekst domyślny jest zawsze zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="be79c-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="be79c-115">Chyba że wyrażenie stałe jest jawnie umieszczone w niezaznaczonej kontekście, przepełnienia, które występują podczas oceny w czasie kompilacji wyrażenia powodować błędy w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="be79c-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="be79c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be79c-116">See also</span></span>

- [<span data-ttu-id="be79c-117">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="be79c-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be79c-118">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="be79c-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be79c-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="be79c-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be79c-120">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="be79c-120">Statement Keywords</span></span>](statement-keywords.md)
