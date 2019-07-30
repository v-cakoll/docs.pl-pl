---
title: Powiązania let w klasach
description: Dowiedz się, jak definiować pola prywatne i prywatne F# funkcje dla klas przy użyciu powiązań "let" w definicji klasy.
ms.date: 05/16/2016
ms.openlocfilehash: 0086d3a91f85395c2bd0555f978c5d951c363357
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627485"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="36b72-103">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="36b72-103">let Bindings in Classes</span></span>

<span data-ttu-id="36b72-104">Można definiować pola prywatne i prywatne funkcje dla F# klas przy użyciu `let` powiązań w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="36b72-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="36b72-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36b72-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="36b72-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36b72-106">Remarks</span></span>

<span data-ttu-id="36b72-107">Poprzednia składnia jest wyświetlana po nagłówku klasy i deklaracji dziedziczenia, ale przed żadną definicją elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="36b72-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="36b72-108">Składnia jest taka sama jak `let` w przypadku powiązań poza klasami, ale nazwy zdefiniowane w klasie mają zakres, który jest ograniczony do klasy.</span><span class="sxs-lookup"><span data-stu-id="36b72-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="36b72-109">`let` Powiązanie tworzy pole prywatne lub funkcję, aby ujawnić dane lub funkcje publicznie, deklaruj właściwość lub metodę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="36b72-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="36b72-110">Powiązanie, które nie jest statyczne jest nazywane powiązaniem `let`wystąpienia. `let`</span><span class="sxs-lookup"><span data-stu-id="36b72-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="36b72-111">Powiązania `let` wystąpień są wykonywane podczas tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="36b72-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="36b72-112">Powiązania `let` statyczne są częścią inicjatora statycznego dla klasy, która jest gwarantowana do wykonania przed pierwszym użyciem typu.</span><span class="sxs-lookup"><span data-stu-id="36b72-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="36b72-113">Kod w powiązaniach `let` wystąpień może używać parametrów konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="36b72-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="36b72-114">Atrybuty i Modyfikatory dostępności są niedozwolone w `let` powiązaniach klas.</span><span class="sxs-lookup"><span data-stu-id="36b72-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="36b72-115">Poniższe przykłady kodu ilustrują kilka typów `let` powiązań w klasach.</span><span class="sxs-lookup"><span data-stu-id="36b72-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="36b72-116">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="36b72-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="36b72-117">Alternatywne sposoby tworzenia pól</span><span class="sxs-lookup"><span data-stu-id="36b72-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="36b72-118">Możesz również użyć słowa kluczowego, `val` aby utworzyć pole prywatne.</span><span class="sxs-lookup"><span data-stu-id="36b72-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="36b72-119">Przy użyciu `val` słowa kluczowego, pole nie otrzymuje wartości podczas tworzenia obiektu, ale zamiast tego jest inicjowane z wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="36b72-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="36b72-120">Aby uzyskać więcej informacji, [Zobacz pola jawne: Val — słowo](explicit-fields-the-val-keyword.md)kluczowe.</span><span class="sxs-lookup"><span data-stu-id="36b72-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="36b72-121">Można również zdefiniować pola prywatne w klasie za pomocą definicji elementu członkowskiego i dodać słowo kluczowe `private` do definicji.</span><span class="sxs-lookup"><span data-stu-id="36b72-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="36b72-122">Może to być przydatne, jeśli zamierzasz zmienić dostępność elementu członkowskiego bez konieczności ponownego pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="36b72-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="36b72-123">Aby uzyskać więcej informacji, zobacz [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="36b72-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="36b72-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36b72-124">See also</span></span>

- [<span data-ttu-id="36b72-125">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="36b72-125">Members</span></span>](index.md)
- [<span data-ttu-id="36b72-126">`do`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="36b72-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="36b72-127">`let`Powiązań</span><span class="sxs-lookup"><span data-stu-id="36b72-127">`let` Bindings</span></span>](../functions/let-bindings.md)
