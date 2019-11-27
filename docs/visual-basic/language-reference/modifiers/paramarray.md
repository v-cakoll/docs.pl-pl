---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: fbc87bffebc265e6062512e96fc29a64334b3c65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351372"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="9181c-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9181c-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="9181c-103">Określa, że parametr procedury przyjmuje opcjonalną tablicę elementów określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9181c-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="9181c-104">`ParamArray` można używać tylko w ostatnim parametrze listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="9181c-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9181c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9181c-105">Remarks</span></span>  
 <span data-ttu-id="9181c-106">`ParamArray` pozwala przekazać dowolną liczbę argumentów do procedury.</span><span class="sxs-lookup"><span data-stu-id="9181c-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="9181c-107">Parametr `ParamArray` jest zawsze deklarowany przy użyciu elementu [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="9181c-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="9181c-108">Do parametru `ParamArray` można podać jeden lub więcej argumentów, przekazując tablicę odpowiedniego typu danych, rozdzieloną przecinkami listę wartości lub nic wcale.</span><span class="sxs-lookup"><span data-stu-id="9181c-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="9181c-109">Aby uzyskać szczegółowe informacje, zobacz "wywoływanie ParamArray" w [tablicach parametrów](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="9181c-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9181c-110">Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9181c-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="9181c-111">Jeśli zaakceptujesz tablicę parametrów z kodu wywołującego, należy przetestować jego długość i wykonać odpowiednie czynności, jeśli jest ono zbyt duże dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9181c-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="9181c-112">Modyfikator `ParamArray` może być używany w tych kontekstach:</span><span class="sxs-lookup"><span data-stu-id="9181c-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9181c-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9181c-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9181c-114">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9181c-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9181c-115">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9181c-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9181c-116">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9181c-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9181c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9181c-117">See also</span></span>

- [<span data-ttu-id="9181c-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9181c-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="9181c-119">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="9181c-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
