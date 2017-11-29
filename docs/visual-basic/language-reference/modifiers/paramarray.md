---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="1fc56-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fc56-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="1fc56-103">Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1fc56-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="1fc56-104">`ParamArray`może być używany tylko ostatni parametr listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="1fc56-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fc56-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fc56-105">Remarks</span></span>  
 <span data-ttu-id="1fc56-106">`ParamArray`Służy do przekazywania dowolnej liczby argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="1fc56-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="1fc56-107">A `ParamArray` parametru jest zawsze zadeklarowane za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="1fc56-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="1fc56-108">Możesz podać jeden lub więcej argumentów `ParamArray` przez przekazanie tablicy odpowiednie dane typ parametru, rozdzielana przecinkami lista wartości lub nic w ogóle.</span><span class="sxs-lookup"><span data-stu-id="1fc56-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="1fc56-109">Aby uzyskać więcej informacji, zobacz "Podczas wywoływania ParamArray" w [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1fc56-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fc56-110">Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1fc56-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="1fc56-111">Jeśli akceptujesz tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1fc56-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="1fc56-112">`ParamArray` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="1fc56-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1fc56-113">DECLARE — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fc56-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1fc56-114">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fc56-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1fc56-115">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fc56-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1fc56-116">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1fc56-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1fc56-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fc56-117">See Also</span></span>  
 [<span data-ttu-id="1fc56-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1fc56-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1fc56-119">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="1fc56-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
