---
title: "Członkowie (F#)"
description: "Informacje o elementach członkowskich obiektu w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="f68fc-104">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f68fc-104">Members</span></span>

<span data-ttu-id="f68fc-105">W tej sekcji opisano elementy członkowskie typów obiektów języka F #.</span><span class="sxs-lookup"><span data-stu-id="f68fc-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="f68fc-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f68fc-106">Remarks</span></span>
<span data-ttu-id="f68fc-107">*Elementy członkowskie* są funkcje, które są częścią definicji typu i został zadeklarowany z `member` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f68fc-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="f68fc-108">Suma rozłączna — obiekt typów F # takich jak rekordy, klasy, Unii, interfejsów, i struktury obsługi elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="f68fc-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="f68fc-109">Aby uzyskać więcej informacji, zobacz [rekordów](../records.md), [klasy](../classes.md), [Suma rozłączna unie](../discriminated-Unions.md), [interfejsów](../interfaces.md), i [struktury](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="f68fc-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="f68fc-110">Elementy członkowskie zwykle składają się interfejsu publicznego dla typu, dlatego są one publiczne, chyba że określono inaczej.</span><span class="sxs-lookup"><span data-stu-id="f68fc-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="f68fc-111">Elementy Członkowskie mogą być deklarowane również w prywatny lub wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="f68fc-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="f68fc-112">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="f68fc-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="f68fc-113">Podpisy dla typów może również służyć do ujawniają i nie ujawnia niektóre elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="f68fc-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="f68fc-114">Aby uzyskać więcej informacji, zobacz [podpisy](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="f68fc-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="f68fc-115">Pól prywatnych i `do` powiązania, które są używane tylko z klasami, nie są członkami wartość true, ponieważ nigdy nie są częścią interfejsu publicznego typu i nie został zadeklarowany z `member` — słowo kluczowe, ale są opisane w tej sekcji również.</span><span class="sxs-lookup"><span data-stu-id="f68fc-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="f68fc-116">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="f68fc-116">Related Topics</span></span>


|<span data-ttu-id="f68fc-117">Temat</span><span class="sxs-lookup"><span data-stu-id="f68fc-117">Topic</span></span>|<span data-ttu-id="f68fc-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f68fc-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="f68fc-119">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="f68fc-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="f68fc-120">Zawiera opis definicji pól prywatnych i funkcje w klasach.</span><span class="sxs-lookup"><span data-stu-id="f68fc-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="f68fc-121">`do`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="f68fc-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="f68fc-122">W tym artykule opisano specyfikację kod inicjujący obiektu.</span><span class="sxs-lookup"><span data-stu-id="f68fc-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="f68fc-123">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f68fc-123">Properties</span></span>](properties.md)|<span data-ttu-id="f68fc-124">Opisuje właściwości członków klasy i innych typów.</span><span class="sxs-lookup"><span data-stu-id="f68fc-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="f68fc-125">Właściwości indeksowane</span><span class="sxs-lookup"><span data-stu-id="f68fc-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="f68fc-126">Opisuje właściwości tablicy w klasami i innymi typami.</span><span class="sxs-lookup"><span data-stu-id="f68fc-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="f68fc-127">Metody</span><span class="sxs-lookup"><span data-stu-id="f68fc-127">Methods</span></span>](methods.md)|<span data-ttu-id="f68fc-128">W tym artykule opisano funkcje, które są elementami członkowskimi typu.</span><span class="sxs-lookup"><span data-stu-id="f68fc-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="f68fc-129">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="f68fc-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="f68fc-130">Opisuje specjalne funkcje, które Inicjowanie obiektów typu.</span><span class="sxs-lookup"><span data-stu-id="f68fc-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="f68fc-131">Przeładowanie operatora</span><span class="sxs-lookup"><span data-stu-id="f68fc-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="f68fc-132">Zawiera opis definicji operatorów niestandardowe dla typów.</span><span class="sxs-lookup"><span data-stu-id="f68fc-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="f68fc-133">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f68fc-133">Events</span></span>](events.md)|<span data-ttu-id="f68fc-134">Zawiera opis definicji zdarzenia i zdarzeń w języku F #.</span><span class="sxs-lookup"><span data-stu-id="f68fc-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="f68fc-135">Pola jawne: `val` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="f68fc-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="f68fc-136">Zawiera opis definicji niezainicjowanej pól w typie.</span><span class="sxs-lookup"><span data-stu-id="f68fc-136">Describes the definition of uninitialized fields in a type.</span></span>|
