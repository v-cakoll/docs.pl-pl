---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: b9dee0fc876c6e7a02d085db7db4bf1c5dd2c68d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816667"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="68b1b-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68b1b-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="68b1b-103">Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="68b1b-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="68b1b-104">`ParamArray` może służyć tylko na ostatni parametr listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="68b1b-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b1b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68b1b-105">Remarks</span></span>  
 <span data-ttu-id="68b1b-106">`ParamArray` można przekazać dowolną liczbę argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="68b1b-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="68b1b-107">A `ParamArray` parametr zawsze jest zadeklarowany za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="68b1b-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="68b1b-108">Możesz podać jeden lub więcej argumentów do `ParamArray` , przekazując tablicę odpowiednie dane typu parametru, rozdzielaną przecinkami listę wartości lub nic w ogóle.</span><span class="sxs-lookup"><span data-stu-id="68b1b-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="68b1b-109">Aby uzyskać szczegółowe informacje, zobacz "Podczas wywoływania ParamArray" w [Parameter — tablice](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="68b1b-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68b1b-110">Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68b1b-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="68b1b-111">Jeśli zdecydujesz się zaakceptować tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmie stosowne działania, jeśli jest zbyt duży dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68b1b-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="68b1b-112">`ParamArray` Modyfikator mogą być używane w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="68b1b-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="68b1b-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="68b1b-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="68b1b-114">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="68b1b-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="68b1b-115">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="68b1b-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="68b1b-116">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="68b1b-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="68b1b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68b1b-117">See also</span></span>

- [<span data-ttu-id="68b1b-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="68b1b-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="68b1b-119">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="68b1b-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
