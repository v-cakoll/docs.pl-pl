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
ms.openlocfilehash: 8fc5d1afd9e9723e6b3c58e100b0519ef8fdfab4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968363"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="b836d-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b836d-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="b836d-103">Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b836d-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="b836d-104">`ParamArray`może być używany tylko dla ostatniego parametru listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="b836d-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b836d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b836d-105">Remarks</span></span>  
 <span data-ttu-id="b836d-106">`ParamArray`umożliwia przekazanie dowolnej liczby argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="b836d-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="b836d-107">Parametr jest zawsze deklarowany przy użyciu [ByVal.](../../../visual-basic/language-reference/modifiers/byval.md) `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="b836d-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="b836d-108">Można podać jeden lub więcej argumentów do `ParamArray` parametru, przekazując tablicę odpowiedniego typu danych, rozdzielaną przecinkami listę wartości lub nic wcale.</span><span class="sxs-lookup"><span data-stu-id="b836d-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="b836d-109">Aby uzyskać szczegółowe informacje, zobacz "wywoływanie ParamArray" w [tablicach parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="b836d-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b836d-110">Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b836d-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="b836d-111">Jeśli zaakceptujesz tablicę parametrów z kodu wywołującego, należy przetestować jego długość i wykonać odpowiednie czynności, jeśli jest ono zbyt duże dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b836d-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="b836d-112">`ParamArray` Modyfikator może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="b836d-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b836d-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b836d-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="b836d-114">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b836d-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b836d-115">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="b836d-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b836d-116">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b836d-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b836d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b836d-117">See also</span></span>

- [<span data-ttu-id="b836d-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b836d-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="b836d-119">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="b836d-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
