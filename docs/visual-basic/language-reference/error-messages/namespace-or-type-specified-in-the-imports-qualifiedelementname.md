---
title: Przestrzeń nazw lub typ określone w elemencie Imports „<qualifiedelementname>” nie zawierają żadnego członka publicznego lub nie można go odnaleźć
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 1873c0af7a251afd7754557f5dcb6aed13eb9f11
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357888"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="6e9b8-102">Namespace lub typ określony w elemencie Imports\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć</span><span class="sxs-lookup"><span data-stu-id="6e9b8-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="6e9b8-103">Namespace lub typ określony w elemencie Imports\<qualifiedelementname >' nie zawiera żadnej publicznej składowej lub nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="6e9b8-104">Upewnij się, że przestrzeń nazw lub typ zostały zdefiniowane i zawierają co najmniej jednego członka publicznego.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="6e9b8-105">Upewnij się, że nazwa aliasu nie zawiera innych aliasów.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="6e9b8-106">`Imports` Instrukcja określa element zawierający, która nie może być odnaleziona lub nie definiuje `Public` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="6e9b8-107">A *zawierającego element* może być przestrzeni nazw, klasy, struktury, moduł, interfejs lub wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="6e9b8-108">Element zawierający zawiera składniki, takie jak zmienne, procedury lub inne elementy zawierające.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="6e9b8-109">Celem importowania jest umożliwienie kodu do elementów członkowskich przestrzeni nazw lub typ dostępu bez ich kwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="6e9b8-110">Dodaj odwołanie do przestrzeni nazw lub typ projektu również może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="6e9b8-111">Aby uzyskać więcej informacji, zobacz "Importowanie zawierający elementy" w [odwołania do elementów zadeklarowany](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="6e9b8-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="6e9b8-112">Jeśli kompilator nie może znaleźć określony element zawierający, nie można go rozpoznać odwołania, które go używają.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="6e9b8-113">W przypadku znalezienia elementu, ale nie ujawnia na dowolny element `Public` elementów członkowskich, a następnie Brak odwołania może odnieść sukces.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="6e9b8-114">W obu przypadkach jest bez znaczenia, aby zaimportować element.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="6e9b8-115">Należy pamiętać, że jeśli import — element zawierający i przypisać aliasu importu, następnie nie możesz użyć tego aliasu importu można zaimportować innego elementu.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="6e9b8-116">Poniższy kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="6e9b8-117">**Identyfikator błędu:** BC40056</span><span class="sxs-lookup"><span data-stu-id="6e9b8-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6e9b8-118">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6e9b8-118">To correct this error</span></span>

1. <span data-ttu-id="6e9b8-119">Sprawdź, czy element zawierający jest dostępny z projektu.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="6e9b8-120">Sprawdź specyfikację elementu zawierającą nie zawiera żadnych aliasu importu z innego importu.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="6e9b8-121">Sprawdź element zawierający ujawnia co najmniej jeden `Public` elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6e9b8-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e9b8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e9b8-122">See also</span></span>

- [<span data-ttu-id="6e9b8-123">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="6e9b8-123">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="6e9b8-124">Namespace, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e9b8-124">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="6e9b8-125">Public</span><span class="sxs-lookup"><span data-stu-id="6e9b8-125">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="6e9b8-126">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6e9b8-126">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="6e9b8-127">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="6e9b8-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
