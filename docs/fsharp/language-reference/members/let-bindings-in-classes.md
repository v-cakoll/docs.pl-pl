---
title: "Powiązania let w klasach (F#)"
description: "Dowiedz się, jak zdefiniować pól prywatnych i prywatne dla klas F # za pomocą powiązania \"let\" w definicji klasy."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9d3710f5-68b1-4e4c-b02b-27fe018f20e8
ms.openlocfilehash: 1337cc0794e366e8c39745f5c45065362c9c38c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="c1605-104">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="c1605-104">let Bindings in Classes</span></span>

<span data-ttu-id="c1605-105">Można zdefiniować pól prywatnych i prywatne dla klas F # za pomocą `let` powiązania w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="c1605-105">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>


## <a name="syntax"></a><span data-ttu-id="c1605-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1605-106">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="c1605-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1605-107">Remarks</span></span>
<span data-ttu-id="c1605-108">Poprzednie składni pojawia się po deklaracjach nagłówek i dziedziczenie klas, ale przed żadnych definicji elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c1605-108">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="c1605-109">Składnia jest na przykład systemu `let` powiązania poza klasy, ale nazw zdefiniowana w klasie mieć zakres, który jest ograniczona do klasy.</span><span class="sxs-lookup"><span data-stu-id="c1605-109">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="c1605-110">A `let` powiązania tworzy pole prywatne lub funkcji; do udostępniania danych lub funkcje deklarować publicznie, właściwości lub metody elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c1605-110">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="c1605-111">A `let` powiązanie nie jest statyczna nosi nazwę wystąpienia `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="c1605-111">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="c1605-112">Wystąpienie `let` powiązania wykonania podczas tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="c1605-112">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="c1605-113">Statyczne `let` powiązania są częścią inicjator statyczny dla klasy, która może wykonać przed pierwszym użyciu typu.</span><span class="sxs-lookup"><span data-stu-id="c1605-113">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="c1605-114">Kod w wystąpieniu `let` powiązania mogą używać parametrów podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="c1605-114">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="c1605-115">Atrybuty i modyfikatory dostępności są niedozwolone w `let` powiązania w klasach.</span><span class="sxs-lookup"><span data-stu-id="c1605-115">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="c1605-116">Poniższe przykłady kodu przedstawiają kilka typów `let` powiązania w klasach.</span><span class="sxs-lookup"><span data-stu-id="c1605-116">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="c1605-117">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="c1605-117">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="c1605-118">Alternatywne metody tworzenia pól</span><span class="sxs-lookup"><span data-stu-id="c1605-118">Alternative Ways to Create Fields</span></span>
<span data-ttu-id="c1605-119">Można również użyć `val` — słowo kluczowe, aby utworzyć pole prywatne.</span><span class="sxs-lookup"><span data-stu-id="c1605-119">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="c1605-120">Korzystając z `val` — słowo kluczowe, pole nie zostanie podany, wartość, gdy obiekt jest tworzony, ale zamiast tego jest zainicjowany z wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="c1605-120">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="c1605-121">Aby uzyskać więcej informacji, zobacz [pola jawne: val — słowo kluczowe](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="c1605-121">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="c1605-122">Można także zdefiniować pól prywatnych w klasie, przy użyciu definicji elementu członkowskiego i dodając słowo kluczowe `private` do definicji.</span><span class="sxs-lookup"><span data-stu-id="c1605-122">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="c1605-123">Może to być przydatne, Jeśli przypuszczasz, że Zmień dostępność elementu członkowskiego bez ponownego tworzenia kodu.</span><span class="sxs-lookup"><span data-stu-id="c1605-123">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="c1605-124">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="c1605-124">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c1605-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1605-125">See Also</span></span>
[<span data-ttu-id="c1605-126">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c1605-126">Members</span></span>](index.md)

[<span data-ttu-id="c1605-127">`do`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="c1605-127">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)

[<span data-ttu-id="c1605-128">`let`Powiązania</span><span class="sxs-lookup"><span data-stu-id="c1605-128">`let` Bindings</span></span>](../functions/let-bindings.md)
