---
title: "Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt;&#39; &#39; t zawierają żadnego członka publicznego lub nie można odnaleźć"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 49cd9fa5d5182b2cf2d7fc4623bc8e9aa02bf85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="e5b51-102">Namespace lub typ określony w elemencie Imports &#39; &lt;qualifiedelementname&gt;&#39; &#39; t zawierają żadnego członka publicznego lub nie można odnaleźć</span><span class="sxs-lookup"><span data-stu-id="e5b51-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="e5b51-103">Namespace lub typ określony w elemencie Imports\<qualifiedelementname >' nie zawierają żadnego członka publicznego lub nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="e5b51-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="e5b51-104">Upewnij się, że przestrzeń nazw lub typ są zdefiniowane i zawierają co najmniej jednego członka publicznego.</span><span class="sxs-lookup"><span data-stu-id="e5b51-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="e5b51-105">Upewnij się, że nazwa aliasu nie zawiera innych aliasów.</span><span class="sxs-lookup"><span data-stu-id="e5b51-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="e5b51-106">`Imports` Instrukcji określa zawierający element, który nie może być odnaleziona albo nie definiuje `Public` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e5b51-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="e5b51-107">A *zawierającego element* może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e5b51-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="e5b51-108">Element zawierający zawiera członków, takie jak zmienne, procedury i innych elementów zawierających.</span><span class="sxs-lookup"><span data-stu-id="e5b51-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="e5b51-109">Importowanie celem jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez konieczności ich kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="e5b51-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="e5b51-110">Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="e5b51-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="e5b51-111">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b51-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="e5b51-112">Jeśli kompilator nie może znaleźć określonego elementu zawierającego, nie można go rozpoznać odwołań, które go używają.</span><span class="sxs-lookup"><span data-stu-id="e5b51-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="e5b51-113">Jeśli znajdzie elementu, ale element nie ujawnia żadnego `Public` elementy członkowskie, a następnie odwołania nie mogą być skutecznie.</span><span class="sxs-lookup"><span data-stu-id="e5b51-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="e5b51-114">W obu przypadkach jest bez znaczenia, aby zaimportować element.</span><span class="sxs-lookup"><span data-stu-id="e5b51-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="e5b51-115">Należy pamiętać, że Jeśli zaimportujesz zawierający element, a następnie przypisać aliasu importu, następnie nie umożliwia tego aliasu importu zaimportować innego elementu.</span><span class="sxs-lookup"><span data-stu-id="e5b51-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="e5b51-116">Poniższy kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e5b51-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="e5b51-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="e5b51-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="e5b51-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="e5b51-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="e5b51-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="e5b51-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="e5b51-120">**Identyfikator błędu:** BC40056</span><span class="sxs-lookup"><span data-stu-id="e5b51-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5b51-121">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e5b51-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="e5b51-122">Sprawdź, czy zawierającego element jest dostępny z projektu.</span><span class="sxs-lookup"><span data-stu-id="e5b51-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="e5b51-123">Sprawdź, czy specyfikację elementu zawierającego nie zawiera żadnych aliasu importu z innego importu.</span><span class="sxs-lookup"><span data-stu-id="e5b51-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="e5b51-124">Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e5b51-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b51-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5b51-125">See Also</span></span>  
 [<span data-ttu-id="e5b51-126">Imports — instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="e5b51-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="e5b51-127">Namespace — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5b51-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="e5b51-128">Publiczna</span><span class="sxs-lookup"><span data-stu-id="e5b51-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="e5b51-129">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5b51-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="e5b51-130">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="e5b51-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
