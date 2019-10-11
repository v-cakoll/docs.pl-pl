---
title: <proceduresignature1> jest niezgodna ze specyfikacją CLS, ponieważ przeciążania <proceduresignature2>, które różnią się tylko tablicą typów parametrów tablicowych lub według rangi typów parametrów tablicy
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250182"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="d976a-102">\<proceduresignature1 > jest niezgodna ze specyfikacją CLS, ponieważ przeciąż \<proceduresignature2 >, które różnią się tylko tablicą typów parametrów tablicowych lub według rangi typów parametrów tablicy</span><span class="sxs-lookup"><span data-stu-id="d976a-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="d976a-103">Procedura lub właściwość jest oznaczona jako `<CLSCompliant(True)>`, gdy zastępuje inną procedurę lub właściwość i jedyną różnicą między ich listami parametrów jest poziom zagnieżdżenia tablicy nieregularnej lub rangi tablicy.</span><span class="sxs-lookup"><span data-stu-id="d976a-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>
  
 <span data-ttu-id="d976a-104">W poniższych deklaracjach druga i trzecia deklaracja generują ten błąd:</span><span class="sxs-lookup"><span data-stu-id="d976a-104">In the following declarations, the second and third declarations generate this error:</span></span>
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 <span data-ttu-id="d976a-105">Druga deklaracja zmienia oryginalny jednowymiarowy parametr `arrayParam` na tablicę tablic.</span><span class="sxs-lookup"><span data-stu-id="d976a-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="d976a-106">Trzecia deklaracja zmienia `arrayParam` na tablicę dwuwymiarową (ranga 2).</span><span class="sxs-lookup"><span data-stu-id="d976a-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="d976a-107">Chociaż Visual Basic zezwala na przeciążenia tylko jednej z tych zmian, takie Przeciążenie nie jest zgodne z [niezależnymi od języka i składnikami niezależnymi od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d976a-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="d976a-108">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, należy ustawić parametr `isCompliant` atrybutu na `True` lub `False`, aby wskazać zgodność lub niezgodność.</span><span class="sxs-lookup"><span data-stu-id="d976a-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d976a-109">Dla tego parametru nie ma wartości domyślnej i należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="d976a-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="d976a-110">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> do elementu, jest on uznawany za niezgodny.</span><span class="sxs-lookup"><span data-stu-id="d976a-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="d976a-111">Domyślnie ten komunikat jest ostrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="d976a-111">By default, this message is a warning.</span></span> <span data-ttu-id="d976a-112">Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d976a-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d976a-113">**Identyfikator błędu:** BC40035</span><span class="sxs-lookup"><span data-stu-id="d976a-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d976a-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d976a-114">To correct this error</span></span>  
  
- <span data-ttu-id="d976a-115">Jeśli jest wymagana zgodność ze specyfikacją CLS, zdefiniuj przeciążenia tak, aby różnią się od siebie na więcej sposobów niż zmiany wprowadzone na tej stronie pomocy.</span><span class="sxs-lookup"><span data-stu-id="d976a-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="d976a-116">Jeśli wymagane jest, aby przeciążenia różniły się tylko zmianami wprowadzonymi na tej stronie pomocy, Usuń <xref:System.CLSCompliantAttribute> z ich definicji lub Oznacz je jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="d976a-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d976a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d976a-117">See also</span></span>

- [<span data-ttu-id="d976a-118">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="d976a-118">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d976a-119">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="d976a-119">Overloads</span></span>](../modifiers/overloads.md)
