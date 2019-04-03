---
title: Niejawna konwersja z „<typename1>” na „<typename2>” podczas kopiowania wartości parametru „ByRef” „<parametername>” z powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: 7b02659d96b08c592b25ddf3ef1f99114c3ee269
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831764"
---
# <a name="implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="ea83c-102">Niejawna konwersja z "\<typename1 >" do "\<typename2 >" podczas kopiowania wartości parametru "ByRef" "\<parametername >" powrotem do pasującego argumentu.</span><span class="sxs-lookup"><span data-stu-id="ea83c-102">Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>
<span data-ttu-id="ea83c-103">Procedura jest wywoływana z [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumentu typu innego niż jego odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="ea83c-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="ea83c-104">W przypadku przekazania argument `ByRef`, Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, zamiast przekazywać odwołania.</span><span class="sxs-lookup"><span data-stu-id="ea83c-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="ea83c-105">W takim przypadku po powrocie z procedury języka Visual Basic należy skopiować do argumentu w wywoływanym kodzie następnie wartości zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="ea83c-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="ea83c-106">Jeśli `ByRef` wartość argumentu jest kopiowana do procedury i parametry i argument są tego samego typu, konwersja nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="ea83c-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="ea83c-107">Jednak w przypadku różnych typów języka Visual Basic należy przekonwertować w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="ea83c-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="ea83c-108">Ponieważ nie można użyć `CType` lub dowolne inne słowa kluczowe konwersji argumentu procedury lub parametr, taka konwersja jest zawsze niejawne.</span><span class="sxs-lookup"><span data-stu-id="ea83c-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="ea83c-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="ea83c-109">By default, this message is a warning.</span></span> <span data-ttu-id="ea83c-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ea83c-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ea83c-111">**Identyfikator błędu:** BC41999</span><span class="sxs-lookup"><span data-stu-id="ea83c-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea83c-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="ea83c-112">To correct this error</span></span>  
  
-   <span data-ttu-id="ea83c-113">Jeśli to możliwe należy użyć wywoływania argumentów tego samego typu jako parametr procedury, Visual Basic nie trzeba wykonać żadnych konwersji.</span><span class="sxs-lookup"><span data-stu-id="ea83c-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="ea83c-114">Jeśli musisz wywołać procedurę z nieprawidłowym argumentem typu różni się od typu parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="ea83c-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea83c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea83c-115">See also</span></span>

- [<span data-ttu-id="ea83c-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="ea83c-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ea83c-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="ea83c-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="ea83c-118">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="ea83c-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="ea83c-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="ea83c-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
