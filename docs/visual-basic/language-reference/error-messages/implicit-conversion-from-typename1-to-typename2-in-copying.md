---
title: Niejawna konwersja z &#39; &lt;typename1&gt; &#39; do &#39; &lt;typename2&gt; &#39; podczas kopiowania wartości &#39;ByRef&#39; parametru &#39; &lt; Nazwa parametru&gt; &#39; powrotem do pasującego argumentu.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="c100f-102">Niejawna konwersja z &#39; &lt;typename1&gt; &#39; do &#39; &lt;typename2&gt; &#39; podczas kopiowania wartości &#39;ByRef&#39; parametru &#39; &lt; Nazwa parametru&gt; &#39; powrotem do pasującego argumentu.</span><span class="sxs-lookup"><span data-stu-id="c100f-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="c100f-103">Procedura jest wywoływana z [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumentu typu innego niż jego odpowiadającego mu parametru.</span><span class="sxs-lookup"><span data-stu-id="c100f-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="c100f-104">Jeśli zostanie przekazany argument `ByRef`, Visual Basic czasami kopiuje wartość argumentu do zmiennej lokalnej w procedurze, a przekazywaniem odwołań do.</span><span class="sxs-lookup"><span data-stu-id="c100f-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="c100f-105">W takim przypadku po powrocie z procedury języka Visual Basic należy skopiować do argumentu w wywoływanym kodzie następnie wartości zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="c100f-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="c100f-106">Jeśli `ByRef` wartość argumentu jest kopiowany do procedury i argumentów i parametrów są tego samego typu, niezbędne jest brak konwersji.</span><span class="sxs-lookup"><span data-stu-id="c100f-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="c100f-107">Ale typy są różne, Visual Basic, należy przekonwertować w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="c100f-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="c100f-108">Ponieważ nie można użyć `CType` lub wszelkie inne słowa kluczowe konwersji na argumentu procedury lub parametrów, takich konwersji zawsze jest niejawnie.</span><span class="sxs-lookup"><span data-stu-id="c100f-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="c100f-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c100f-109">By default, this message is a warning.</span></span> <span data-ttu-id="c100f-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c100f-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c100f-111">**Identyfikator błędu:** BC41999</span><span class="sxs-lookup"><span data-stu-id="c100f-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c100f-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c100f-112">To correct this error</span></span>  
  
-   <span data-ttu-id="c100f-113">Jeśli to możliwe należy użyć wywoływania argumentów tego samego typu jako parametru procedury dzięki Visual Basic nie trzeba wykonać żadnej konwersji.</span><span class="sxs-lookup"><span data-stu-id="c100f-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="c100f-114">Jeśli musisz wywołać procedurę z argumentem Typ inny niż typ parametru, ale nie muszą zwracać wartość do wywołującego argumentu, zdefiniuj dany parametr jako [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) zamiast `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="c100f-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c100f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c100f-115">See Also</span></span>  
 [<span data-ttu-id="c100f-116">Procedury</span><span class="sxs-lookup"><span data-stu-id="c100f-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="c100f-117">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="c100f-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c100f-118">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="c100f-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="c100f-119">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c100f-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
