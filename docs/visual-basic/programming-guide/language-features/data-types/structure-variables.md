---
title: Zmienne struktur
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 16b6cdc5a849b50f6caa8b7963dac5c12d63cf3e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346306"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="cdee4-102">Zmienne struktur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdee4-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="cdee4-103">Po utworzeniu struktury można zadeklarować zmienne poziomu procedury i na poziomie modułu jako ten typ.</span><span class="sxs-lookup"><span data-stu-id="cdee4-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="cdee4-104">Można na przykład utworzyć strukturę, która rejestruje informacje o systemie komputerowym.</span><span class="sxs-lookup"><span data-stu-id="cdee4-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="cdee4-105">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="cdee4-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="cdee4-106">Można teraz zadeklarować zmienne tego typu.</span><span class="sxs-lookup"><span data-stu-id="cdee4-106">You can now declare variables of that type.</span></span> <span data-ttu-id="cdee4-107">Ilustruje to poniższą deklarację.</span><span class="sxs-lookup"><span data-stu-id="cdee4-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="cdee4-108">W klasach i modułach struktury zadeklarowane przy użyciu [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) są domyślne dla dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="cdee4-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="cdee4-109">Jeśli zamierzasz mieć prywatną strukturę, upewnij się, że deklarujesz ją przy użyciu [prywatnego](../../../../visual-basic/language-reference/modifiers/private.md) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cdee4-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="cdee4-110">Dostęp do wartości struktury</span><span class="sxs-lookup"><span data-stu-id="cdee4-110">Access to Structure Values</span></span>

<span data-ttu-id="cdee4-111">Aby przypisać i pobrać wartości z elementów zmiennej struktury, należy użyć tej samej składni, która jest używana do ustawiania i pobierania właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cdee4-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="cdee4-112">Operator dostępu do elementów członkowskich (`.`) należy umieścić między nazwą zmiennej struktury a nazwą elementu.</span><span class="sxs-lookup"><span data-stu-id="cdee4-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="cdee4-113">Poniższy przykład uzyskuje dostęp do elementów zmiennych zadeklarowanych wcześniej jako typ `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="cdee4-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="cdee4-114">Przypisywanie zmiennych struktury</span><span class="sxs-lookup"><span data-stu-id="cdee4-114">Assigning Structure Variables</span></span>

<span data-ttu-id="cdee4-115">Można również przypisać jedną zmienną do innej, jeśli oba są tego samego typu struktury.</span><span class="sxs-lookup"><span data-stu-id="cdee4-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="cdee4-116">Spowoduje to skopiowanie wszystkich elementów jednej struktury do odpowiednich elementów w drugim.</span><span class="sxs-lookup"><span data-stu-id="cdee4-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="cdee4-117">Ilustruje to poniższą deklarację.</span><span class="sxs-lookup"><span data-stu-id="cdee4-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="cdee4-118">Jeśli element struktury jest typem referencyjnym, takim jak `String`, `Object`lub Array, wskaźnik do danych jest kopiowany.</span><span class="sxs-lookup"><span data-stu-id="cdee4-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="cdee4-119">W poprzednim przykładzie, jeśli `systemInfo` zawierała zmienną obiektu, poprzedni przykład skopiował wskaźnik z `mySystem` do `yourSystem`, a zmiana danych obiektu za pomocą jednej struktury będzie miała wpływ na dostęp za pośrednictwem innej struktury.</span><span class="sxs-lookup"><span data-stu-id="cdee4-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdee4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdee4-120">See also</span></span>

- [<span data-ttu-id="cdee4-121">Typy danych</span><span class="sxs-lookup"><span data-stu-id="cdee4-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="cdee4-122">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="cdee4-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="cdee4-123">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="cdee4-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="cdee4-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="cdee4-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="cdee4-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="cdee4-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cdee4-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="cdee4-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="cdee4-127">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="cdee4-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="cdee4-128">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="cdee4-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="cdee4-129">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="cdee4-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="cdee4-130">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cdee4-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
