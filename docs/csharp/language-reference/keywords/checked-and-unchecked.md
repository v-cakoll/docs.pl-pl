---
title: Zaznaczone i niezaznaczone — C# odwołanie
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 7abc19e0657330752e7798d060516c48aa402297
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771776"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="50365-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="50365-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="50365-103">C#instrukcje mogą być wykonywane w kontekście zaznaczonym lub niezaznaczonym.</span><span class="sxs-lookup"><span data-stu-id="50365-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="50365-104">W kontekście, przepełnienie arytmetyczne wywołuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="50365-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="50365-105">W kontekście niesprawdzonym przepełnienie arytmetyczne jest ignorowane, a wynik zostanie obcięty przez odrzucenie wszystkich bitów o dużej kolejności, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="50365-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="50365-106">[zaznaczone](checked.md) Określ sprawdzony kontekst.</span><span class="sxs-lookup"><span data-stu-id="50365-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="50365-107">[niezaznaczone](unchecked.md) Określ kontekst niesprawdzony.</span><span class="sxs-lookup"><span data-stu-id="50365-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="50365-108">Sprawdzanie przepełnienia ma wpływ na następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="50365-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="50365-109">Wyrażenia wykorzystujące następujące wstępnie zdefiniowane operatory w typach całkowitych:</span><span class="sxs-lookup"><span data-stu-id="50365-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="50365-110">`++`, `--`, `-` jednoargumentowy, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="50365-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="50365-111">Jawne konwersje liczbowe między typami całkowitymi lub z `float` lub `double` do typu całkowitego.</span><span class="sxs-lookup"><span data-stu-id="50365-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="50365-112">Jeśli nie `checked` ani `unchecked` jest określony, domyślny kontekst dla wyrażeń niestałych (wyrażenia, które są oceniane w czasie wykonywania) jest zdefiniowany przez wartość opcji kompilatora [-Checked](../compiler-options/checked-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="50365-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="50365-113">Domyślnie wartość tej opcji to unoptional, a operacje arytmetyczne są wykonywane w niesprawdzonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="50365-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="50365-114">W przypadku wyrażeń stałych (wyrażenia, które mogą być w pełni oceniane w czasie kompilacji), domyślnym kontekstem jest zawsze zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="50365-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="50365-115">Jeśli wyrażenie stałe nie jest jawnie umieszczane w niesprawdzonym kontekście, przepełnienie następuje podczas obliczania czasu kompilacji wyrażenia powodującego błędy czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="50365-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="50365-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50365-116">See also</span></span>

- [<span data-ttu-id="50365-117">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="50365-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50365-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50365-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50365-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="50365-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50365-120">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="50365-120">Statement Keywords</span></span>](statement-keywords.md)
