---
title: "Nazwa &lt;namespacename&gt; w głównej przestrzeni nazw &lt;fullnamespacename&gt; nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7342c7e85cce6c0e5892c4ad1826907dc03ed808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="81bdb-102">Nazwa &lt;namespacename&gt; w głównej przestrzeni nazw &lt;fullnamespacename&gt; nie jest zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="81bdb-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="81bdb-103">Zestaw jest oznaczony jako `<CLSCompliant(True)>`, ale element nazwy głównej przestrzeni nazw rozpoczyna się od znaku podkreślenia (`_`).</span><span class="sxs-lookup"><span data-stu-id="81bdb-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="81bdb-104">Element programowania może zawierać jeden lub więcej znaków podkreślenia, ale aby było zgodne z [niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3) (ze specyfikacją CLS) musi nie zaczynać się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="81bdb-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="81bdb-105">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="81bdb-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="81bdb-106">Po zastosowaniu <xref:System.CLSCompliantAttribute> do elementu programistycznego, ten atrybut zostanie ustawiony `isCompliant` albo parametr `True` lub `False` zgodności lub niezgodności.</span><span class="sxs-lookup"><span data-stu-id="81bdb-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="81bdb-107">Nie jest domyślnie dla tego parametru, a należy podać wartość.</span><span class="sxs-lookup"><span data-stu-id="81bdb-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="81bdb-108">Jeśli nie mają zastosowania <xref:System.CLSCompliantAttribute> do elementu, jest uznawane za niezgodne.</span><span class="sxs-lookup"><span data-stu-id="81bdb-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="81bdb-109">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="81bdb-109">By default, this message is a warning.</span></span> <span data-ttu-id="81bdb-110">Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="81bdb-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="81bdb-111">**Identyfikator błędu:** BC40039</span><span class="sxs-lookup"><span data-stu-id="81bdb-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81bdb-112">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="81bdb-112">To correct this error</span></span>  
  
-   <span data-ttu-id="81bdb-113">Jeśli potrzebujesz zgodności ze specyfikacją CLS, Zmień nazwy głównej przestrzeni nazw, tak, aby żaden z elementów jego rozpoczyna się od znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="81bdb-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="81bdb-114">Jeśli potrzebujesz zmieniają nazwę przestrzeni nazw, następnie usuń <xref:System.CLSCompliantAttribute> z zestawu lub Oznacz go jako `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="81bdb-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bdb-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81bdb-115">See Also</span></span>  
 [<span data-ttu-id="81bdb-116">Namespace — instrukcja</span><span class="sxs-lookup"><span data-stu-id="81bdb-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="81bdb-117">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81bdb-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="81bdb-118">/ rootnamespace</span><span class="sxs-lookup"><span data-stu-id="81bdb-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [<span data-ttu-id="81bdb-119">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81bdb-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="81bdb-120">Zadeklarowane nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="81bdb-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="81bdb-121">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="81bdb-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="81bdb-122">\<PAVE za pośrednictwem > Pisanie kodu zgodne ze specyfikacją CLS</span><span class="sxs-lookup"><span data-stu-id="81bdb-122">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
