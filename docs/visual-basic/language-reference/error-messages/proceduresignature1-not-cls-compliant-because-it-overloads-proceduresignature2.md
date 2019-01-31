---
title: Element „<proceduresignature1>” nie jest zgodny ze specyfikacją CLS, ponieważ przeciąża element „<proceduresignature2>”, który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269565"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="5cff8-102">\<proceduresignature1 > nie jest zgodny ze specyfikacją CLS, ponieważ przeciąża \<proceduresignature2 > który różni się od niego tylko tablicą typów parametrów tablicowych lub rangą typów parametrów tablicowych</span><span class="sxs-lookup"><span data-stu-id="5cff8-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="5cff8-103">Procedura lub właściwość jest oznaczona jako `<CLSCompliant(True)>` po zastępuje ona inny procedura lub właściwość, a jedyną różnicą między swoimi listami parametr jest poziom zagnieżdżenia tablicy nieregularnej lub rangę tablicy.</span><span class="sxs-lookup"><span data-stu-id="5cff8-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="5cff8-104">W następujące deklaracje deklaracje drugi i trzeci generuje ten błąd.</span><span class="sxs-lookup"><span data-stu-id="5cff8-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="5cff8-105">Drugi deklaracja zmienia pierwotny parametr jednowymiarowa `arrayParam` do tablicy tablic.</span><span class="sxs-lookup"><span data-stu-id="5cff8-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="5cff8-106">Trzeci zmiany deklaracji `arrayParam` dwuwymiarowej tablicy (ranga 2).</span><span class="sxs-lookup"><span data-stu-id="5cff8-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="5cff8-107">Chociaż Visual Basic umożliwia przeciążenia, które mogą się różnić tylko przez jeden z tych zmian, takich przeciążenie nie jest zgodne z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="5cff8-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="5cff8-108">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="5cff8-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5cff8-109">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="5cff8-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5cff8-110">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="5cff8-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5cff8-111">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5cff8-111">By default, this message is a warning.</span></span> <span data-ttu-id="5cff8-112">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5cff8-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5cff8-113">**Identyfikator błędu:** BC40035</span><span class="sxs-lookup"><span data-stu-id="5cff8-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5cff8-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="5cff8-114">To correct this error</span></span>  
  
-   <span data-ttu-id="5cff8-115">Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zdefiniować swoje przeciążenia mogą się różnić od siebie nawzajem na więcej sposobów niż tylko zmiany wymienione na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="5cff8-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="5cff8-116">Jeśli potrzebujesz, że przeciążenia różnią się tylko przez zmiany wymienione w tej pomocy strony, Usuń <xref:System.CLSCompliantAttribute> ze swojej definicji lub oznaczyć je jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="5cff8-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cff8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cff8-117">See also</span></span>

- [<span data-ttu-id="5cff8-118">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="5cff8-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="5cff8-119">Overloads</span><span class="sxs-lookup"><span data-stu-id="5cff8-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
