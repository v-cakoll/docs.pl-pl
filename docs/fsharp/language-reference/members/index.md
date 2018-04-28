---
title: Członkowie (F#)
description: 'Informacje o elementach członkowskich obiektu w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a37f14d138cc017cf78e3a0ff1d5b5bba2f09020
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="members"></a><span data-ttu-id="4b7ad-103">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4b7ad-103">Members</span></span>

<span data-ttu-id="4b7ad-104">W tej sekcji opisano elementy członkowskie typów obiektów języka F #.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-104">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="4b7ad-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b7ad-105">Remarks</span></span>
<span data-ttu-id="4b7ad-106">*Elementy członkowskie* są funkcje, które są częścią definicji typu i został zadeklarowany z `member` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="4b7ad-107">Suma rozłączna — obiekt typów F # takich jak rekordy, klasy, Unii, interfejsów, i struktury obsługi elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="4b7ad-108">Aby uzyskać więcej informacji, zobacz [rekordów](../records.md), [klasy](../classes.md), [Suma rozłączna unie](../discriminated-Unions.md), [interfejsów](../interfaces.md), i [struktury](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ad-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="4b7ad-109">Elementy członkowskie zwykle składają się interfejsu publicznego dla typu, dlatego są one publiczne, chyba że określono inaczej.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="4b7ad-110">Elementy Członkowskie mogą być deklarowane również w prywatny lub wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="4b7ad-111">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ad-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="4b7ad-112">Podpisy dla typów może również służyć do ujawniają i nie ujawnia niektóre elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="4b7ad-113">Aby uzyskać więcej informacji, zobacz [podpisy](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="4b7ad-113">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="4b7ad-114">Pól prywatnych i `do` powiązania, które są używane tylko z klasami, nie są członkami wartość true, ponieważ nigdy nie są częścią interfejsu publicznego typu i nie został zadeklarowany z `member` — słowo kluczowe, ale są opisane w tej sekcji również.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="4b7ad-115">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="4b7ad-115">Related Topics</span></span>


|<span data-ttu-id="4b7ad-116">Temat</span><span class="sxs-lookup"><span data-stu-id="4b7ad-116">Topic</span></span>|<span data-ttu-id="4b7ad-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4b7ad-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="4b7ad-118">`let` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="4b7ad-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="4b7ad-119">Zawiera opis definicji pól prywatnych i funkcje w klasach.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="4b7ad-120">`do` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="4b7ad-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="4b7ad-121">W tym artykule opisano specyfikację kod inicjujący obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="4b7ad-122">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4b7ad-122">Properties</span></span>](properties.md)|<span data-ttu-id="4b7ad-123">Opisuje właściwości członków klasy i innych typów.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="4b7ad-124">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="4b7ad-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="4b7ad-125">Opisuje właściwości tablicy w klasami i innymi typami.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="4b7ad-126">Metody</span><span class="sxs-lookup"><span data-stu-id="4b7ad-126">Methods</span></span>](methods.md)|<span data-ttu-id="4b7ad-127">W tym artykule opisano funkcje, które są elementami członkowskimi typu.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="4b7ad-128">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="4b7ad-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="4b7ad-129">Opisuje specjalne funkcje, które Inicjowanie obiektów typu.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="4b7ad-130">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="4b7ad-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="4b7ad-131">Zawiera opis definicji operatorów niestandardowe dla typów.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="4b7ad-132">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4b7ad-132">Events</span></span>](events.md)|<span data-ttu-id="4b7ad-133">Zawiera opis definicji zdarzenia i zdarzeń w języku F #.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="4b7ad-134">Pola jawne: słowo kluczowe `val`</span><span class="sxs-lookup"><span data-stu-id="4b7ad-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="4b7ad-135">Zawiera opis definicji niezainicjowanej pól w typie.</span><span class="sxs-lookup"><span data-stu-id="4b7ad-135">Describes the definition of uninitialized fields in a type.</span></span>|
