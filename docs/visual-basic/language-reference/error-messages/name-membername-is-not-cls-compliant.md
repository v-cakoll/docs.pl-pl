---
title: Nazwa &lt;membername&gt; nie jest zgodne ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 26ff13de461d5a96724868b7928129a326cdf1d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="e02d0-102">Nazwa &lt;membername&gt; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="e02d0-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="e02d0-103">Zestaw jest oznaczony jako `<CLSCompliant(True)>` , ale udostępnia element członkowski o nazwie, która rozpoczyna się od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="e02d0-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="e02d0-104">Element programowania może zawierać jeden lub więcej znaków podkreślenia, ale aby było zgodne z [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS) musi nie zaczynać się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e02d0-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="e02d0-105">Zobacz temat[Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e02d0-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="e02d0-106">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="e02d0-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="e02d0-107">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="e02d0-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="e02d0-108">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="e02d0-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="e02d0-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="e02d0-109">By default, this message is a warning.</span></span> <span data-ttu-id="e02d0-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e02d0-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e02d0-111">**Identyfikator błędu:** BC40031</span><span class="sxs-lookup"><span data-stu-id="e02d0-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e02d0-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e02d0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="e02d0-113">Jeśli masz kontrolę kodu źródłowego, Zmień nazwę elementu członkowskiego, tak, aby nie zaczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="e02d0-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="e02d0-114">Jeśli potrzebujesz, że nazwa elementu członkowskiego pozostają niezmienione, Usuń <xref:System.CLSCompliantAttribute> z jego definicji lub Oznacz go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="e02d0-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="e02d0-115">Można nadal Oznacz zestaw jako `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="e02d0-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02d0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e02d0-116">See Also</span></span>  
 [<span data-ttu-id="e02d0-117">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="e02d0-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="e02d0-118">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="e02d0-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  

