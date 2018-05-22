---
title: checked i unchecked (odwołanie w C#)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: f8e292a67fab49b5fc3616e438d063eca2617274
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="f4f32-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f4f32-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="f4f32-103">C# instrukcje mogą wykonywać w kontekście zaznaczać lub usuwać zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="f4f32-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="f4f32-104">W kontekście zaznaczone przepełnienia arytmetycznego zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f4f32-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="f4f32-105">W kontekście niezaznaczone przepełnienia arytmetycznego jest ignorowana, a wynik został obcięty odrzucając wszystkie najbardziej znaczących bitów, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="f4f32-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="f4f32-106">[zaznaczone](checked.md) kontekstu Określ zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f4f32-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="f4f32-107">[Zaznaczenie opcji](unchecked.md) Określ niezaznaczone kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f4f32-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="f4f32-108">Sprawdzanie przepełnienia dotyczy następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="f4f32-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="f4f32-109">Za pomocą następujących operatorów wstępnie zdefiniowane na typy całkowite wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="f4f32-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="f4f32-110">`++`, `--`, jednoargumentowy `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="f4f32-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="f4f32-111">Jawne konwersje liczbowe między typów całkowitych lub z `float` lub `double` na typ całkowity.</span><span class="sxs-lookup"><span data-stu-id="f4f32-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="f4f32-112">Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst dla wyrażenia niestałego (wyrażeń, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość [-zaznaczone](../compiler-options/checked-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f4f32-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f4f32-113">Domyślnie jest nie ustawiono wartość tej opcji i operacje arytmetyczne są wykonywane w kontekście niezaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f4f32-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="f4f32-114">Dla wyrażenia stałe (wyrażeń, które może przyjąć pełni w czasie kompilacji) domyślny kontekst jest zawsze zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f4f32-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="f4f32-115">Jeśli wyrażenie stałe jest jawnie umieszczona w kontekście niezaznaczone, przepełnienia, jakie występują podczas obliczania kompilacji wyrażenia spowodować błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f4f32-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f4f32-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4f32-116">See Also</span></span>  
 [<span data-ttu-id="f4f32-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f4f32-117">C# Reference</span></span>](../index.md)  
 [<span data-ttu-id="f4f32-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f4f32-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="f4f32-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f4f32-119">C# Keywords</span></span>](index.md)  
 [<span data-ttu-id="f4f32-120">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="f4f32-120">Statement Keywords</span></span>](statement-keywords.md)
