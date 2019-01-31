---
title: Nazwa <namespacename> w głównej przestrzeni nazw <fullnamespacename> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: c5afdcc98b7acb1927c9b0735a69fbe64c3d8e60
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268720"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="4d315-102">Nazwa \<namespacename > w głównej przestrzeni nazw \<fullnamespacename > nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="4d315-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="4d315-103">Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element główna nazwa przestrzeni nazw, który rozpoczyna się od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="4d315-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="4d315-104">Programowania element może zawierać jeden lub więcej podkreślenia, ale aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), należy nie zaczyna się ona od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="4d315-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="4d315-105">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4d315-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="4d315-106">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="4d315-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="4d315-107">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="4d315-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="4d315-108">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="4d315-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="4d315-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="4d315-109">By default, this message is a warning.</span></span> <span data-ttu-id="4d315-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4d315-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4d315-111">**Identyfikator błędu:** BC40039</span><span class="sxs-lookup"><span data-stu-id="4d315-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d315-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="4d315-112">To correct this error</span></span>  
  
-   <span data-ttu-id="4d315-113">Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zmienić główna nazwa przestrzeni nazw, aby żaden z jej elementów zaczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="4d315-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="4d315-114">Jeśli potrzebujesz, że nazwa przestrzeni nazw pozostają niezmienione, następnie usuń <xref:System.CLSCompliantAttribute> z zestawu lub oznaczyć go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="4d315-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d315-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d315-115">See also</span></span>
- [<span data-ttu-id="4d315-116">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="4d315-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="4d315-117">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d315-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="4d315-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="4d315-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="4d315-119">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d315-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="4d315-120">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="4d315-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="4d315-121">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="4d315-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

