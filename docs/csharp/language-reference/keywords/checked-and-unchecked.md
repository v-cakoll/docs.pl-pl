---
title: "checked i unchecked (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="30bce-102">checked i unchecked (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="30bce-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="30bce-103">C# instrukcje mogą wykonywać w kontekście zaznaczać lub usuwać zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="30bce-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="30bce-104">W kontekście zaznaczone przepełnienia arytmetycznego zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="30bce-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="30bce-105">W kontekście niezaznaczone przepełnienia arytmetycznego jest ignorowana, a wynik został obcięty.</span><span class="sxs-lookup"><span data-stu-id="30bce-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated.</span></span>  
  
-   <span data-ttu-id="30bce-106">[zaznaczone](../../../csharp/language-reference/keywords/checked.md) kontekstu Określ zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="30bce-106">[checked](../../../csharp/language-reference/keywords/checked.md) Specify checked context.</span></span>  
  
-   <span data-ttu-id="30bce-107">[Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md) Określ niezaznaczone kontekstu.</span><span class="sxs-lookup"><span data-stu-id="30bce-107">[unchecked](../../../csharp/language-reference/keywords/unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="30bce-108">Jeśli żadna `checked` ani `unchecked` określono domyślny kontekst zależy od czynników zewnętrznych, takich jak opcje kompilatora.</span><span class="sxs-lookup"><span data-stu-id="30bce-108">If neither `checked` nor `unchecked` is specified, the default context depends on external factors such as compiler options.</span></span>  
  
 <span data-ttu-id="30bce-109">Sprawdzanie przepełnienia dotyczy następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="30bce-109">The following operations are affected by the overflow checking:</span></span>  
  
-   <span data-ttu-id="30bce-110">Za pomocą następujących operatorów wstępnie zdefiniowane na typy całkowite wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="30bce-110">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="30bce-111">`++``--` -(jednoargumentowy) `+`  -    `*``/`</span><span class="sxs-lookup"><span data-stu-id="30bce-111">`++` `--` - (unary)   `+` -   `*` `/`</span></span>  
  
-   <span data-ttu-id="30bce-112">Jawne konwersje liczbowe między typów całkowitych.</span><span class="sxs-lookup"><span data-stu-id="30bce-112">Explicit numeric conversions between integral types.</span></span>  
  
 <span data-ttu-id="30bce-113">[/ Checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) — opcja kompilatora pozwala określić zaznaczenie kontekst dla wszystkich instrukcji arytmetyczne liczba całkowita, które nie są jawnie w zakresie `checked` lub `unchecked` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="30bce-113">The [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) compiler option lets you specify checked or unchecked context for all integer arithmetic statements that are not explicitly in the scope of a `checked` or `unchecked` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bce-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30bce-114">See Also</span></span>  
 [<span data-ttu-id="30bce-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="30bce-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="30bce-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30bce-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30bce-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="30bce-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="30bce-118">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="30bce-118">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)
