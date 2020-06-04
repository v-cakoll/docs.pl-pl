---
title: Przestrzeń nazw lub typ określone w elemencie Imports „<qualifiedelementname>” nie zawierają żadnego członka publicznego lub nie można go odnaleźć
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409468"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="d0637-102">Przestrzeń nazw lub typ określone w elemencie Imports „\<qualifiedelementname>” nie zawierają żadnego członka publicznego lub nie można go odnaleźć</span><span class="sxs-lookup"><span data-stu-id="d0637-102">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="d0637-103">Przestrzeń nazw lub typ określony w elemencie Imports " \<qualifiedelementname> " nie zawiera żadnej publicznej składowej lub nie można jej znaleźć.</span><span class="sxs-lookup"><span data-stu-id="d0637-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="d0637-104">Upewnij się, że przestrzeń nazw lub typ jest zdefiniowany i zawiera co najmniej jedną publiczną składową.</span><span class="sxs-lookup"><span data-stu-id="d0637-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="d0637-105">Upewnij się, że Nazwa aliasu nie zawiera innych aliasów.</span><span class="sxs-lookup"><span data-stu-id="d0637-105">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="d0637-106">`Imports`Instrukcja określa element zawierający, którego nie można odnaleźć lub nie definiuje żadnych `Public` elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d0637-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="d0637-107">*Element zawierający* może być przestrzenią nazw, klasą, strukturą, modułem, interfejsem lub wyliczeniem.</span><span class="sxs-lookup"><span data-stu-id="d0637-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="d0637-108">Element zawierający zawiera elementy członkowskie, takie jak zmienne, procedury lub inne elementy zawierające.</span><span class="sxs-lookup"><span data-stu-id="d0637-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="d0637-109">Celem importowania jest umożliwienie kodowi dostępu do przestrzeni nazw lub typów elementów członkowskich bez konieczności kwalifikowania się do nich.</span><span class="sxs-lookup"><span data-stu-id="d0637-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="d0637-110">W projekcie może być również konieczne dodanie odwołania do przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="d0637-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="d0637-111">Aby uzyskać więcej informacji, zobacz "Importowanie zawierających elementy" w [odniesieniu do zadeklarowanych elementów](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="d0637-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="d0637-112">Jeśli kompilator nie może znaleźć określonego elementu zawierającego, wówczas nie może rozpoznać odwołań, które go używają.</span><span class="sxs-lookup"><span data-stu-id="d0637-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="d0637-113">Jeśli odnajdzie element, ale element nie ujawnia żadnych `Public` elementów członkowskich, odwołanie nie może się powieść.</span><span class="sxs-lookup"><span data-stu-id="d0637-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="d0637-114">W obu przypadkach nie ma znaczenia, aby zaimportować element.</span><span class="sxs-lookup"><span data-stu-id="d0637-114">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="d0637-115">Należy pamiętać, że w przypadku zaimportowania elementu zawierającego i przypisania do niego aliasu importu nie można użyć tego aliasu importu do zaimportowania innego elementu.</span><span class="sxs-lookup"><span data-stu-id="d0637-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="d0637-116">Poniższy kod generuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d0637-116">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="d0637-117">**Identyfikator błędu:** BC40056</span><span class="sxs-lookup"><span data-stu-id="d0637-117">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d0637-118">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d0637-118">To correct this error</span></span>

1. <span data-ttu-id="d0637-119">Sprawdź, czy element zawierający jest dostępny z projektu.</span><span class="sxs-lookup"><span data-stu-id="d0637-119">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="d0637-120">Sprawdź, czy Specyfikacja elementu zawierającego nie zawiera żadnego aliasu importu z innego importu.</span><span class="sxs-lookup"><span data-stu-id="d0637-120">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="d0637-121">Sprawdź, czy zawierający element uwidacznia co najmniej jeden `Public` element członkowski.</span><span class="sxs-lookup"><span data-stu-id="d0637-121">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0637-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0637-122">See also</span></span>

- [<span data-ttu-id="d0637-123">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="d0637-123">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="d0637-124">Namespace — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="d0637-124">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="d0637-125">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="d0637-125">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="d0637-126">Przestrzenie nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0637-126">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="d0637-127">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="d0637-127">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
