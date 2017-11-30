---
title: "Pola jawne: val — Słowo kluczowe (F#)"
description: "Dowiedz się więcej o F # \"val\" — słowo kluczowe, które służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury bez zainicjowania typu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="d147d-104">Pola jawne: val — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="d147d-104">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="d147d-105">`val` — Słowo kluczowe służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="d147d-105">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="d147d-106">Zadeklarowany w ten sposób lokalizacji przechowywania są nazywane *pola jawne*.</span><span class="sxs-lookup"><span data-stu-id="d147d-106">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="d147d-107">Użycie innego `val` — słowo kluczowe jest używana razem z `member` słowo kluczowe, aby zadeklarować właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d147d-107">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="d147d-108">Aby uzyskać więcej informacji na temat właściwości zaimplementowane automatycznie, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="d147d-108">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="d147d-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d147d-109">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="d147d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d147d-110">Remarks</span></span>
<span data-ttu-id="d147d-111">Zwykły sposób, aby zdefiniować pól w typie klasy lub struktury jest użycie `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="d147d-111">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="d147d-112">Jednak `let` powiązania musi zostać zainicjowany jako część konstruktora klasy, która nie jest zawsze możliwe, wymagane lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="d147d-112">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="d147d-113">Można użyć `val` — słowo kluczowe, jeśli chcesz pola, które nie jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="d147d-113">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="d147d-114">Pola jawne mogą być statyczne lub statyczna.</span><span class="sxs-lookup"><span data-stu-id="d147d-114">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="d147d-115">*Modyfikator dostępu* może być `public`, `private`, lub `internal`.</span><span class="sxs-lookup"><span data-stu-id="d147d-115">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="d147d-116">Domyślnie pola jawne są publiczne.</span><span class="sxs-lookup"><span data-stu-id="d147d-116">By default, explicit fields are public.</span></span> <span data-ttu-id="d147d-117">To różni się od `let` powiązania w klasach, które są zawsze prywatne.</span><span class="sxs-lookup"><span data-stu-id="d147d-117">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="d147d-118">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atrybut jest wymagany dla pola jawne w typach klas, które mają podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d147d-118">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="d147d-119">Ten atrybut określa, czy pole ustawiana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="d147d-119">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="d147d-120">Typ pola musi obsługiwać inicjowania zero.</span><span class="sxs-lookup"><span data-stu-id="d147d-120">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="d147d-121">Typem obsługuje inicjowania zero, jeśli jest to jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="d147d-121">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="d147d-122">Pierwotny typ, który ma wartość zerową.</span><span class="sxs-lookup"><span data-stu-id="d147d-122">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="d147d-123">Typ, który obsługuje wartość null albo jako wartość normalne, jako wartość nieprawidłowego lub jako reprezentację wartości.</span><span class="sxs-lookup"><span data-stu-id="d147d-123">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="d147d-124">Dotyczy to również klas, krotek, rekordy, funkcji, interfejsów, typów referencyjnych .NET, `unit` typu i typy Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="d147d-124">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="d147d-125">Typ wartości .NET.</span><span class="sxs-lookup"><span data-stu-id="d147d-125">A .NET value type.</span></span>

- <span data-ttu-id="d147d-126">Struktury, którego wszystkie pola obsługiwać wartość domyślną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="d147d-126">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="d147d-127">Na przykład modyfikować pola o nazwie `someField` został skompilowany polem zapasowym w ramach platformy .NET reprezentacja o nazwie `someField@`, uzyskasz dostęp do wartości przechowywanej za pomocą właściwości o nazwie `someField`.</span><span class="sxs-lookup"><span data-stu-id="d147d-127">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="d147d-128">Dla pola modyfikowalnego reprezentacja skompilowana .NET jest polem .NET.</span><span class="sxs-lookup"><span data-stu-id="d147d-128">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="d147d-129">`Note`Przestrzeń nazw .NET Framework `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="d147d-129">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="d147d-130">Informacje dla tego atrybutu, zobacz `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d147d-130">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="d147d-131">Poniższy kod przedstawia użycie pola jawne oraz do porównania, `let` powiązania w klasie, która ma podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d147d-131">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="d147d-132">Należy pamiętać, że `let`— pole powiązane `myInt1` jest prywatny.</span><span class="sxs-lookup"><span data-stu-id="d147d-132">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="d147d-133">Gdy `let`— pole powiązane `myInt1` jest wywoływany przez metodę elementu członkowskiego własnego identyfikatora `this` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d147d-133">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="d147d-134">Jednak gdy utworzono odwołanie do pola jawne `myInt2` i `myString`, własnego identyfikatora jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d147d-134">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="d147d-135">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="d147d-135">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="d147d-136">Poniższy kod przedstawia jawne pola w klasie, która nie ma podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d147d-136">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="d147d-137">W takim przypadku `DefaultValue` atrybut nie jest wymagana, ale wszystkie pola muszą zostać zainicjowane w konstruktorach, które są zdefiniowane dla typu.</span><span class="sxs-lookup"><span data-stu-id="d147d-137">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="d147d-138">Dane wyjściowe `35 22`.</span><span class="sxs-lookup"><span data-stu-id="d147d-138">The output is `35 22`.</span></span>

<span data-ttu-id="d147d-139">Poniższy kod przedstawia jawne pola w strukturze.</span><span class="sxs-lookup"><span data-stu-id="d147d-139">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="d147d-140">Ponieważ struktura jest typem wartości, automatycznie ma domyślny konstruktor, który ustawia wartości pól na zero.</span><span class="sxs-lookup"><span data-stu-id="d147d-140">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="d147d-141">W związku z tym `DefaultValue` atrybut nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d147d-141">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="d147d-142">Dane wyjściowe `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="d147d-142">The output is `11 xyz`.</span></span>

<span data-ttu-id="d147d-143">Pola jawne nie są przeznaczone do użytku rutynowych.</span><span class="sxs-lookup"><span data-stu-id="d147d-143">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="d147d-144">Ogólnie rzecz biorąc, gdy jest to możliwe należy używać `let` powiązania w klasie zamiast jawnego pola.</span><span class="sxs-lookup"><span data-stu-id="d147d-144">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="d147d-145">Pola jawne są przydatne w niektórych scenariuszach współdziałanie, np. gdy są potrzebne do definiowania struktury, który będzie używany w platformie wywołania wywołania do natywnego API ani w zastosowaniach międzyoperacyjnego COM.</span><span class="sxs-lookup"><span data-stu-id="d147d-145">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="d147d-146">Aby uzyskać więcej informacji, zobacz [funkcji zewnętrznych](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d147d-146">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="d147d-147">Innej sytuacji, w którym jawne pole może być konieczne jest podczas pracy z F # generatora kodu który emituje klas bez podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d147d-147">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="d147d-148">Pola jawne są także przydatne zmienne statyczne dla wątku lub podobne konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="d147d-148">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="d147d-149">Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d147d-149">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="d147d-150">Gdy słowa kluczowe `member val` występować razem w definicji typu, jest automatycznie implementowanej właściwości definicji.</span><span class="sxs-lookup"><span data-stu-id="d147d-150">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="d147d-151">Aby uzyskać więcej informacji, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="d147d-151">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="d147d-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d147d-152">See Also</span></span>
[<span data-ttu-id="d147d-153">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d147d-153">Properties</span></span>](properties.md)

[<span data-ttu-id="d147d-154">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d147d-154">Members</span></span>](index.md)

[<span data-ttu-id="d147d-155">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="d147d-155">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
