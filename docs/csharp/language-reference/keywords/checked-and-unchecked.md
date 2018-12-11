---
title: Checked i Unchecked — C# odwołania
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
ms.openlocfilehash: ba4ddd7fa87eb200de0de3aea6f0bc056a40f0e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235811"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="f7f51-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f7f51-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="f7f51-103">Instrukcje języka C# można wykonać w kontekście zaznaczony lub niezaznaczony.</span><span class="sxs-lookup"><span data-stu-id="f7f51-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="f7f51-104">W kontekście sprawdzanym przepełnienie arytmetyczne zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f7f51-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="f7f51-105">W kontekście niesprawdzanym przepełnienie arytmetyczne jest ignorowana, a wynik został obcięty przez odrzucenie wszelkich najbardziej znaczących bitów, które nie mieszczą się w typie docelowym.</span><span class="sxs-lookup"><span data-stu-id="f7f51-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
-   <span data-ttu-id="f7f51-106">[zaznaczone](checked.md) kontekstu Określ zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="f7f51-106">[checked](checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="f7f51-107">[unchecked](unchecked.md) kontekście niesprawdzanym Określ.</span><span class="sxs-lookup"><span data-stu-id="f7f51-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="f7f51-108">Następujące operacje dotyczy sprawdzanie przepełnienia:</span><span class="sxs-lookup"><span data-stu-id="f7f51-108">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="f7f51-109">Za pomocą następujących operatorów wstępnie zdefiniowane na typach całkowitoliczbowych wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="f7f51-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="f7f51-110">`++`, `--`, jednoargumentowe `-`, `+`, `-`, `*`, `/`</span><span class="sxs-lookup"><span data-stu-id="f7f51-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
-   <span data-ttu-id="f7f51-111">Jawnych konwersji liczbowych między typami całkowitymi lub z `float` lub `double` na typ całkowitoliczbowy.</span><span class="sxs-lookup"><span data-stu-id="f7f51-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="f7f51-112">Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst dla wyrażenia stałą (wyrażeń, które są oceniane w czasie wykonywania) jest definiowany przez wartość [-zaznaczone](../compiler-options/checked-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f7f51-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f7f51-113">Domyślnie ustawiono wartość tej opcji, a operacje arytmetyczne są wykonywane w kontekście niesprawdzanym.</span><span class="sxs-lookup"><span data-stu-id="f7f51-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="f7f51-114">Domyślny kontekst zawsze jest sprawdzane dla wyrażeń stałych (wyrażenia, które mogą być w pełni obliczane w czasie kompilacji).</span><span class="sxs-lookup"><span data-stu-id="f7f51-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="f7f51-115">O ile nie jest wyrażeniem stałym jawnie znajduje się w kontekście niesprawdzanym, przepełnienia, które występują podczas obliczania kompilacji wyrażenia spowodować błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f7f51-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f7f51-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7f51-116">See Also</span></span>  

- [<span data-ttu-id="f7f51-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f7f51-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="f7f51-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f7f51-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="f7f51-119">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f7f51-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="f7f51-120">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="f7f51-120">Statement Keywords</span></span>](statement-keywords.md)
