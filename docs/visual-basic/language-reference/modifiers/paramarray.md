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
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597363"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="3dd9a-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dd9a-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="3dd9a-103">Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="3dd9a-104">`ParamArray` może być używany tylko ostatni parametr listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd9a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dd9a-105">Remarks</span></span>  
 <span data-ttu-id="3dd9a-106">`ParamArray` Służy do przekazywania dowolnej liczby argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="3dd9a-107">A `ParamArray` parametru jest zawsze zadeklarowane za pomocą [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="3dd9a-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="3dd9a-108">Możesz podać jeden lub więcej argumentów `ParamArray` przez przekazanie tablicy odpowiednie dane typ parametru, rozdzielana przecinkami lista wartości lub nic w ogóle.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="3dd9a-109">Aby uzyskać więcej informacji, zobacz "Podczas wywoływania ParamArray" w [tablice parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="3dd9a-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3dd9a-110">Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="3dd9a-111">Jeśli akceptujesz tablicy parametrów z kodu wywołującego, należy przetestować jego długość i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3dd9a-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="3dd9a-112">`ParamArray` Modyfikatora można używać w tych sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="3dd9a-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3dd9a-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd9a-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="3dd9a-114">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd9a-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3dd9a-115">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd9a-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="3dd9a-116">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dd9a-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3dd9a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dd9a-117">See Also</span></span>  
 [<span data-ttu-id="3dd9a-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="3dd9a-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="3dd9a-119">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="3dd9a-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
