---
title: Niejawna konwersja z „<typename1>” na „<typename2>” podczas kopiowania wartości parametru „ByRef” „<parametername>” z powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 4d0f9aac795f683cf58210ea38b3783e451ccfc3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402865"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="7d76d-102">Niejawna konwersja z „\<typename1>” na „\<typename2>” podczas kopiowania wartości parametru „ByRef” „\<parametername>” z powrotem do pasującego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d76d-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="7d76d-103">Procedura jest wywoływana z argumentem [ByRef](../modifiers/byref.md) innego typu niż odpowiedni parametr.</span><span class="sxs-lookup"><span data-stu-id="7d76d-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="7d76d-104">W przypadku przekazania argumentu `ByRef` Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołanie.</span><span class="sxs-lookup"><span data-stu-id="7d76d-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="7d76d-105">W takim przypadku, gdy procedura zwraca, Visual Basic należy skopiować wartość zmiennej lokalnej z powrotem do argumentu w kodzie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="7d76d-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="7d76d-106">Jeśli `ByRef` wartość argumentu jest kopiowana do procedury, a argument i parametr są tego samego typu, konwersja nie jest konieczna.</span><span class="sxs-lookup"><span data-stu-id="7d76d-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="7d76d-107">Ale jeśli typy są różne, Visual Basic muszą być konwertowane w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="7d76d-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="7d76d-108">Ponieważ nie można używać `CType` ani żadnych innych słów kluczowych konwersji dla argumentu lub parametru procedury, taka konwersja jest zawsze niejawna.</span><span class="sxs-lookup"><span data-stu-id="7d76d-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="7d76d-109">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="7d76d-109">By default, this message is a warning.</span></span> <span data-ttu-id="7d76d-110">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7d76d-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7d76d-111">**Identyfikator błędu:** BC41999</span><span class="sxs-lookup"><span data-stu-id="7d76d-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7d76d-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="7d76d-112">To correct this error</span></span>  
  
- <span data-ttu-id="7d76d-113">Jeśli to możliwe, użyj argumentu wywołującego tego samego typu co parametr procedury, więc Visual Basic nie musi wykonywać żadnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="7d76d-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
- <span data-ttu-id="7d76d-114">Jeśli musisz wywołać procedurę z typem argumentu innym niż typ parametru, ale nie musisz zwracać wartości do argumentu wywołującego, zdefiniuj parametr jako [ByVal](../modifiers/byval.md) zamiast `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="7d76d-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d76d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d76d-115">See also</span></span>

- [<span data-ttu-id="7d76d-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="7d76d-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="7d76d-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="7d76d-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7d76d-118">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="7d76d-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="7d76d-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="7d76d-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
