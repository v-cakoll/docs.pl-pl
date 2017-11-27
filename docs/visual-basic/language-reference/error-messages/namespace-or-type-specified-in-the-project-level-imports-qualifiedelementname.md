---
title: "Namespace lub typ określony w elemencie Imports poziom projektu &#39; &lt;qualifiedelementname&gt;&#39; &#39; t zawierają żadnego członka publicznego lub nie można odnaleźć"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords: BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d0a164562524af239b3b130f681dbc6eff23814
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="9c54f-102">Namespace lub typ określony w elemencie Imports poziom projektu &#39; &lt;qualifiedelementname&gt;&#39; &#39; t zawierają żadnego członka publicznego lub nie można odnaleźć</span><span class="sxs-lookup"><span data-stu-id="9c54f-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="9c54f-103">Namespace lub typ określony w elemencie Imports poziom projektu\<qualifiedelementname >' nie zawierają żadnego członka publicznego lub nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="9c54f-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="9c54f-104">Upewnij się, że przestrzeń nazw lub typ są zdefiniowane i zawierają co najmniej jednego członka publicznego.</span><span class="sxs-lookup"><span data-stu-id="9c54f-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="9c54f-105">Upewnij się, że nazwa aliasu nie zawiera innych aliasów.</span><span class="sxs-lookup"><span data-stu-id="9c54f-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="9c54f-106">Właściwość importu projektu określa zawierający element, który nie może być odnaleziona albo nie definiuje `Public` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="9c54f-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="9c54f-107">A *zawierającego element* może być w przestrzeni nazw, klasy, struktury, modułu, interfejsu lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9c54f-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="9c54f-108">Element zawierający zawiera członków, takie jak zmienne, procedury i innych elementów zawierających.</span><span class="sxs-lookup"><span data-stu-id="9c54f-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="9c54f-109">Importowanie celem jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez konieczności ich kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="9c54f-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="9c54f-110">Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="9c54f-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="9c54f-111">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="9c54f-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="9c54f-112">Jeśli kompilator nie może znaleźć określonego elementu zawierającego, nie można go rozpoznać odwołań, które go używają.</span><span class="sxs-lookup"><span data-stu-id="9c54f-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="9c54f-113">Jeśli znajdzie elementu, ale element nie ujawnia żadnego `Public` elementy członkowskie, a następnie odwołania nie mogą być skutecznie.</span><span class="sxs-lookup"><span data-stu-id="9c54f-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="9c54f-114">W obu przypadkach jest bez znaczenia, aby zaimportować element.</span><span class="sxs-lookup"><span data-stu-id="9c54f-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="9c54f-115">Możesz użyć **projektanta projektu** do określania elementów do importowania.</span><span class="sxs-lookup"><span data-stu-id="9c54f-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="9c54f-116">Użyj **importowane przestrzenie nazw** sekcji **odwołania** strony.</span><span class="sxs-lookup"><span data-stu-id="9c54f-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="9c54f-117">Aby uzyskać **projektanta projektu** przez dwukrotne kliknięcie **mój projekt** ikonę w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9c54f-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="9c54f-118">**Identyfikator błędu:** BC40057</span><span class="sxs-lookup"><span data-stu-id="9c54f-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c54f-119">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9c54f-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="9c54f-120">Otwórz **projektanta projektu** i przejdź do **odwołania** strony.</span><span class="sxs-lookup"><span data-stu-id="9c54f-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="9c54f-121">W **importowane przestrzenie nazw** upewnij się, że zawierającego element jest dostępny z projektu.</span><span class="sxs-lookup"><span data-stu-id="9c54f-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="9c54f-122">Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="9c54f-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c54f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c54f-123">See Also</span></span>  
 [<span data-ttu-id="9c54f-124">Strona odwołań, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c54f-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)  
 [<span data-ttu-id="9c54f-125">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="9c54f-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="9c54f-126">Publiczna</span><span class="sxs-lookup"><span data-stu-id="9c54f-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="9c54f-127">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c54f-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="9c54f-128">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="9c54f-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
