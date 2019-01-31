---
title: Przestrzeń nazw lub typ określony w elemencie Imports „<qualifiedelementname>” na poziomie projektu nie zawierają żadnego członka publicznego lub nie można go odnaleźć
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 12d20a88179a3d0c93c18f0aed65ca46b001059a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283312"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="a462a-102">Namespace lub typ określony w elemencie Imports na poziomie projektu\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć</span><span class="sxs-lookup"><span data-stu-id="a462a-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="a462a-103">Namespace lub typ określony w elemencie Imports na poziomie projektu\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="a462a-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="a462a-104">Upewnij się, że przestrzeń nazw lub typ zostały zdefiniowane i zawierają co najmniej jednego członka publicznego.</span><span class="sxs-lookup"><span data-stu-id="a462a-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="a462a-105">Upewnij się, że nazwa aliasu nie zawiera innych aliasów.</span><span class="sxs-lookup"><span data-stu-id="a462a-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="a462a-106">Właściwość importowania projektu określa element zawierający, która nie może być odnaleziona lub nie definiuje `Public` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a462a-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="a462a-107">A *zawierającego element* może być przestrzeni nazw, klasy, struktury, moduł, interfejs lub wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a462a-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="a462a-108">Element zawierający zawiera składniki, takie jak zmienne, procedury lub inne elementy zawierające.</span><span class="sxs-lookup"><span data-stu-id="a462a-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="a462a-109">Celem importowania jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez ich kwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="a462a-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="a462a-110">Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="a462a-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="a462a-111">Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="a462a-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="a462a-112">Jeśli kompilator nie może znaleźć określony element zawierający, nie można go rozpoznać odwołania, które go używają.</span><span class="sxs-lookup"><span data-stu-id="a462a-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="a462a-113">W przypadku znalezienia elementu, ale nie ujawnia na dowolny element `Public` elementów członkowskich, a następnie Brak odwołania może odnieść sukces.</span><span class="sxs-lookup"><span data-stu-id="a462a-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="a462a-114">W obu przypadkach jest bez znaczenia, aby zaimportować element.</span><span class="sxs-lookup"><span data-stu-id="a462a-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="a462a-115">Możesz użyć **projektanta projektu** do określania elementów do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="a462a-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="a462a-116">Użyj **zaimportowane przestrzenie nazw** części **odwołania** strony.</span><span class="sxs-lookup"><span data-stu-id="a462a-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="a462a-117">Aby przejść do **projektanta projektu** przez dwukrotne kliknięcie **mój projekt** ikony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a462a-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="a462a-118">**Identyfikator błędu:** BC40057</span><span class="sxs-lookup"><span data-stu-id="a462a-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a462a-119">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a462a-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="a462a-120">Otwórz **projektanta projektu** i przełącz się do **odwołania** strony.</span><span class="sxs-lookup"><span data-stu-id="a462a-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="a462a-121">W **zaimportowane przestrzenie nazw** sekcji, upewnij się, że element zawierający jest dostępny z projektu.</span><span class="sxs-lookup"><span data-stu-id="a462a-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="a462a-122">Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a462a-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a462a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a462a-123">See also</span></span>
- [<span data-ttu-id="a462a-124">Strona odwołań, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a462a-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="a462a-125">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a462a-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="a462a-126">Public</span><span class="sxs-lookup"><span data-stu-id="a462a-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="a462a-127">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a462a-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="a462a-128">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="a462a-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
