---
title: Zmienne struktur
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 270e8ca26185e4a68def3b95f4ce6ab4c57a629c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393588"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="6e28b-102">Zmienne struktur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e28b-102">Structure Variables (Visual Basic)</span></span>

<span data-ttu-id="6e28b-103">Po utworzeniu struktury można zadeklarować zmienne poziomu procedury i na poziomie modułu jako ten typ.</span><span class="sxs-lookup"><span data-stu-id="6e28b-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="6e28b-104">Można na przykład utworzyć strukturę, która rejestruje informacje o systemie komputerowym.</span><span class="sxs-lookup"><span data-stu-id="6e28b-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="6e28b-105">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="6e28b-105">The following example demonstrates this.</span></span>

```vb
Public Structure systemInfo
    Public cPU As String
    Public memory As Long
    Public purchaseDate As Date
End Structure
```

<span data-ttu-id="6e28b-106">Można teraz zadeklarować zmienne tego typu.</span><span class="sxs-lookup"><span data-stu-id="6e28b-106">You can now declare variables of that type.</span></span> <span data-ttu-id="6e28b-107">Ilustruje to poniższą deklarację.</span><span class="sxs-lookup"><span data-stu-id="6e28b-107">The following declaration illustrates this.</span></span>

```vb
Dim mySystem, yourSystem As systemInfo
```

> [!NOTE]
> <span data-ttu-id="6e28b-108">W klasach i modułach struktury zadeklarowane przy użyciu [instrukcji Dim](../../../language-reference/statements/dim-statement.md) są domyślne dla dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="6e28b-108">In classes and modules, structures declared using the [Dim Statement](../../../language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="6e28b-109">Jeśli zamierzasz mieć prywatną strukturę, upewnij się, że deklarujesz ją przy użyciu [prywatnego](../../../language-reference/modifiers/private.md) słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="6e28b-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../language-reference/modifiers/private.md) keyword.</span></span>

## <a name="access-to-structure-values"></a><span data-ttu-id="6e28b-110">Dostęp do wartości struktury</span><span class="sxs-lookup"><span data-stu-id="6e28b-110">Access to Structure Values</span></span>

<span data-ttu-id="6e28b-111">Aby przypisać i pobrać wartości z elementów zmiennej struktury, należy użyć tej samej składni, która jest używana do ustawiania i pobierania właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="6e28b-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="6e28b-112">Należy umieścić operator dostępu do składowej ( `.` ) między nazwą zmiennej struktury i nazwą elementu.</span><span class="sxs-lookup"><span data-stu-id="6e28b-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="6e28b-113">Poniższy przykład uzyskuje dostęp do elementów zmiennych zadeklarowanych wcześniej jako typ `systemInfo` .</span><span class="sxs-lookup"><span data-stu-id="6e28b-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>

```vb
mySystem.cPU = "486"
Dim tooOld As Boolean
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True
```

## <a name="assigning-structure-variables"></a><span data-ttu-id="6e28b-114">Przypisywanie zmiennych struktury</span><span class="sxs-lookup"><span data-stu-id="6e28b-114">Assigning Structure Variables</span></span>

<span data-ttu-id="6e28b-115">Można również przypisać jedną zmienną do innej, jeśli oba są tego samego typu struktury.</span><span class="sxs-lookup"><span data-stu-id="6e28b-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="6e28b-116">Spowoduje to skopiowanie wszystkich elementów jednej struktury do odpowiednich elementów w drugim.</span><span class="sxs-lookup"><span data-stu-id="6e28b-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="6e28b-117">Ilustruje to poniższą deklarację.</span><span class="sxs-lookup"><span data-stu-id="6e28b-117">The following declaration illustrates this.</span></span>

```vb
yourSystem = mySystem
```

<span data-ttu-id="6e28b-118">Jeśli element struktury jest typem referencyjnym, takim jak `String` , `Object` , lub tablicą, wskaźnik do danych jest kopiowany.</span><span class="sxs-lookup"><span data-stu-id="6e28b-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="6e28b-119">W poprzednim przykładzie, jeśli zawierała `systemInfo` zmienną obiektu, poprzedni przykład skopiował wskaźnik z `mySystem` do `yourSystem` , a zmiana danych obiektu za pomocą jednej struktury będzie obowiązywać w przypadku uzyskania dostępu za pośrednictwem innej struktury.</span><span class="sxs-lookup"><span data-stu-id="6e28b-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e28b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e28b-120">See also</span></span>

- [<span data-ttu-id="6e28b-121">Typy danych</span><span class="sxs-lookup"><span data-stu-id="6e28b-121">Data Types</span></span>](index.md)
- [<span data-ttu-id="6e28b-122">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="6e28b-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="6e28b-123">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="6e28b-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="6e28b-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="6e28b-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="6e28b-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="6e28b-125">Structures</span></span>](structures.md)
- [<span data-ttu-id="6e28b-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="6e28b-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="6e28b-127">Instrukcje: Deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="6e28b-127">How to: Declare a Structure</span></span>](how-to-declare-a-structure.md)
- [<span data-ttu-id="6e28b-128">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="6e28b-128">Structures and Other Programming Elements</span></span>](structures-and-other-programming-elements.md)
- [<span data-ttu-id="6e28b-129">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="6e28b-129">Structures and Classes</span></span>](structures-and-classes.md)
- [<span data-ttu-id="6e28b-130">Structure — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e28b-130">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
