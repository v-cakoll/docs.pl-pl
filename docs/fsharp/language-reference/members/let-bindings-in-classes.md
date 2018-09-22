---
title: Powiązania let w klasach (F#)
description: 'Dowiedz się, jak zdefiniować pola prywatne i prywatne funkcje dla klas F # za pomocą powiązania "let" w definicji klasy.'
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46576721"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="2c380-103">Powiązania let w klasach</span><span class="sxs-lookup"><span data-stu-id="2c380-103">let Bindings in Classes</span></span>

<span data-ttu-id="2c380-104">Można zdefiniować pola prywatne i prywatne funkcje dla klas F # za pomocą `let` powiązania w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="2c380-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="2c380-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c380-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="2c380-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c380-106">Remarks</span></span>

<span data-ttu-id="2c380-107">Składnia poprzednich pojawia się po deklaracjach nagłówek i dziedziczenie klasy, ale przed wszystkie definicje elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="2c380-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="2c380-108">Składnia jest podobne do metody `let` powiązania poza klasy, ale nazw zdefiniowana w klasie mają zakres, który jest ograniczony do klasy.</span><span class="sxs-lookup"><span data-stu-id="2c380-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="2c380-109">A `let` powiązania tworzy pole prywatne lub funkcję; aby uwidocznić dane lub funkcje deklarować publicznie, właściwość lub metoda elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2c380-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="2c380-110">A `let` powiązanie nie jest statyczna nosi nazwę wystąpienia `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="2c380-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="2c380-111">Wystąpienie `let` powiązania wykonania podczas tworzenia obiektów.</span><span class="sxs-lookup"><span data-stu-id="2c380-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="2c380-112">Statyczne `let` powiązania są częścią statycznego inicjatora dla klasy, która jest gwarantowane do wykonania przed pierwszym użyciu typu.</span><span class="sxs-lookup"><span data-stu-id="2c380-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="2c380-113">Kod w wystąpieniu `let` powiązania, można użyć parametrów konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="2c380-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="2c380-114">Atrybuty i modyfikatory dostępności nie są dozwolone w `let` powiązania w klasach.</span><span class="sxs-lookup"><span data-stu-id="2c380-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="2c380-115">W poniższych przykładach kodu pokazano kilka typów `let` powiązania w klasach.</span><span class="sxs-lookup"><span data-stu-id="2c380-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="2c380-116">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="2c380-116">The output is as follows.</span></span>

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="2c380-117">Alternatywne sposoby tworzenia pól</span><span class="sxs-lookup"><span data-stu-id="2c380-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="2c380-118">Można również użyć `val` — słowo kluczowe, aby utworzyć pole prywatne.</span><span class="sxs-lookup"><span data-stu-id="2c380-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="2c380-119">Korzystając z `val` — słowo kluczowe, pole nie zostanie podany wartość, gdy obiekt zostanie utworzony, ale zamiast tego jest inicjowany z wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="2c380-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="2c380-120">Aby uzyskać więcej informacji, zobacz [pola jawne: val — słowo kluczowe](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="2c380-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="2c380-121">Można również definiować pola prywatne w klasie, przy użyciu definicji elementu członkowskiego i dodanie słowa kluczowego `private` do definicji.</span><span class="sxs-lookup"><span data-stu-id="2c380-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="2c380-122">Może to być przydatne, jeśli spodziewasz się Zmień dostępność elementu członkowskiego, bez konieczności ponownego zapisu kodu.</span><span class="sxs-lookup"><span data-stu-id="2c380-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="2c380-123">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="2c380-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c380-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c380-124">See also</span></span>

- [<span data-ttu-id="2c380-125">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2c380-125">Members</span></span>](index.md)
- [<span data-ttu-id="2c380-126">`do` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="2c380-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="2c380-127">`let` Powiązania</span><span class="sxs-lookup"><span data-stu-id="2c380-127">`let` Bindings</span></span>](../functions/let-bindings.md)
