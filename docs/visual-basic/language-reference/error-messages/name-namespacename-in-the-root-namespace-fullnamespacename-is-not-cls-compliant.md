---
title: Nazwa <namespacename> w głównej przestrzeni nazw <fullnamespacename> jest niezgodna ze specyfikacją CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: faed46eaf21513945ef4eb0c76d36780e960d380
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592025"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="0407c-102">Nazwa \<namespacename > w głównej przestrzeni nazw \<fullnamespacename > nie jest zgodny ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="0407c-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>
<span data-ttu-id="0407c-103">Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element główna nazwa przestrzeni nazw, który rozpoczyna się od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="0407c-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="0407c-104">Programowania element może zawierać jeden lub więcej podkreślenia, ale aby zachować zgodność z [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), należy nie zaczyna się ona od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="0407c-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0407c-105">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0407c-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="0407c-106">Po zastosowaniu <xref:System.CLSCompliantAttribute> elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` aby wskazać, zgodności ani niezgodności.</span><span class="sxs-lookup"><span data-stu-id="0407c-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0407c-107">Nie istnieje domyślny dla tego parametru. Ponadto należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="0407c-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0407c-108">Jeśli nie zastosujesz <xref:System.CLSCompliantAttribute> elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="0407c-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0407c-109">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="0407c-109">By default, this message is a warning.</span></span> <span data-ttu-id="0407c-110">Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0407c-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0407c-111">**Identyfikator błędu:** BC40039</span><span class="sxs-lookup"><span data-stu-id="0407c-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0407c-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0407c-112">To correct this error</span></span>  
  
- <span data-ttu-id="0407c-113">Jeśli wymagana jest zgodność ze specyfikacją CLS, należy zmienić główna nazwa przestrzeni nazw, aby żaden z jej elementów zaczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="0407c-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="0407c-114">Jeśli potrzebujesz, że nazwa przestrzeni nazw pozostają niezmienione, następnie usuń <xref:System.CLSCompliantAttribute> z zestawu lub oznaczyć go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="0407c-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0407c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0407c-115">See also</span></span>

- [<span data-ttu-id="0407c-116">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0407c-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="0407c-117">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0407c-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="0407c-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0407c-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="0407c-119">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0407c-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="0407c-120">Nazwy zadeklarowanych elementów</span><span class="sxs-lookup"><span data-stu-id="0407c-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="0407c-121">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="0407c-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
