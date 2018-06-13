---
title: 'Pola jawne: val — Słowo kluczowe (F#)'
description: 'Dowiedz się więcej o F # "val" — słowo kluczowe, które służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury bez zainicjowania typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 2bd1aae24a5823ddcd6bb8f121d8110f4a211a6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565824"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="54a98-103">Pola jawne: val — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="54a98-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="54a98-104">`val` — Słowo kluczowe służy do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="54a98-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="54a98-105">Zadeklarowany w ten sposób lokalizacji przechowywania są nazywane *pola jawne*.</span><span class="sxs-lookup"><span data-stu-id="54a98-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="54a98-106">Użycie innego `val` — słowo kluczowe jest używana razem z `member` słowo kluczowe, aby zadeklarować właściwości zaimplementowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="54a98-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="54a98-107">Aby uzyskać więcej informacji na temat właściwości zaimplementowane automatycznie, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="54a98-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="54a98-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="54a98-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="54a98-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54a98-109">Remarks</span></span>
<span data-ttu-id="54a98-110">Zwykły sposób, aby zdefiniować pól w typie klasy lub struktury jest użycie `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="54a98-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="54a98-111">Jednak `let` powiązania musi zostać zainicjowany jako część konstruktora klasy, która nie jest zawsze możliwe, wymagane lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="54a98-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="54a98-112">Można użyć `val` — słowo kluczowe, jeśli chcesz pola, które nie jest zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="54a98-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="54a98-113">Pola jawne mogą być statyczne lub statyczna.</span><span class="sxs-lookup"><span data-stu-id="54a98-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="54a98-114">*Modyfikator dostępu* może być `public`, `private`, lub `internal`.</span><span class="sxs-lookup"><span data-stu-id="54a98-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="54a98-115">Domyślnie pola jawne są publiczne.</span><span class="sxs-lookup"><span data-stu-id="54a98-115">By default, explicit fields are public.</span></span> <span data-ttu-id="54a98-116">To różni się od `let` powiązania w klasach, które są zawsze prywatne.</span><span class="sxs-lookup"><span data-stu-id="54a98-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="54a98-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atrybut jest wymagany dla pola jawne w typach klas, które mają podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="54a98-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="54a98-118">Ten atrybut określa, czy pole ustawiana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="54a98-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="54a98-119">Typ pola musi obsługiwać inicjowania zero.</span><span class="sxs-lookup"><span data-stu-id="54a98-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="54a98-120">Typem obsługuje inicjowania zero, jeśli jest to jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="54a98-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="54a98-121">Pierwotny typ, który ma wartość zerową.</span><span class="sxs-lookup"><span data-stu-id="54a98-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="54a98-122">Typ, który obsługuje wartość null albo jako wartość normalne, jako wartość nieprawidłowego lub jako reprezentację wartości.</span><span class="sxs-lookup"><span data-stu-id="54a98-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="54a98-123">Dotyczy to również klas, krotek, rekordy, funkcji, interfejsów, typów referencyjnych .NET, `unit` typu i typy Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="54a98-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="54a98-124">Typ wartości .NET.</span><span class="sxs-lookup"><span data-stu-id="54a98-124">A .NET value type.</span></span>

- <span data-ttu-id="54a98-125">Struktury, którego wszystkie pola obsługiwać wartość domyślną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="54a98-125">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="54a98-126">Na przykład modyfikować pola o nazwie `someField` został skompilowany polem zapasowym w ramach platformy .NET reprezentacja o nazwie `someField@`, uzyskasz dostęp do wartości przechowywanej za pomocą właściwości o nazwie `someField`.</span><span class="sxs-lookup"><span data-stu-id="54a98-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="54a98-127">Dla pola modyfikowalnego reprezentacja skompilowana .NET jest polem .NET.</span><span class="sxs-lookup"><span data-stu-id="54a98-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="54a98-128">`Note` Przestrzeń nazw .NET Framework `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="54a98-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="54a98-129">Informacje dla tego atrybutu, zobacz `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="54a98-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="54a98-130">Poniższy kod przedstawia użycie pola jawne oraz do porównania, `let` powiązania w klasie, która ma podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="54a98-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="54a98-131">Należy pamiętać, że `let`— pole powiązane `myInt1` jest prywatny.</span><span class="sxs-lookup"><span data-stu-id="54a98-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="54a98-132">Gdy `let`— pole powiązane `myInt1` jest wywoływany przez metodę elementu członkowskiego własnego identyfikatora `this` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="54a98-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="54a98-133">Jednak gdy utworzono odwołanie do pola jawne `myInt2` i `myString`, własnego identyfikatora jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="54a98-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="54a98-134">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="54a98-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="54a98-135">Poniższy kod przedstawia jawne pola w klasie, która nie ma podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="54a98-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="54a98-136">W takim przypadku `DefaultValue` atrybut nie jest wymagana, ale wszystkie pola muszą zostać zainicjowane w konstruktorach, które są zdefiniowane dla typu.</span><span class="sxs-lookup"><span data-stu-id="54a98-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="54a98-137">Dane wyjściowe `35 22`.</span><span class="sxs-lookup"><span data-stu-id="54a98-137">The output is `35 22`.</span></span>

<span data-ttu-id="54a98-138">Poniższy kod przedstawia jawne pola w strukturze.</span><span class="sxs-lookup"><span data-stu-id="54a98-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="54a98-139">Ponieważ struktura jest typem wartości, automatycznie ma domyślny konstruktor, który ustawia wartości pól na zero.</span><span class="sxs-lookup"><span data-stu-id="54a98-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="54a98-140">W związku z tym `DefaultValue` atrybut nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="54a98-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="54a98-141">Dane wyjściowe `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="54a98-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="54a98-142">Pola jawne nie są przeznaczone do użytku rutynowych.</span><span class="sxs-lookup"><span data-stu-id="54a98-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="54a98-143">Ogólnie rzecz biorąc, gdy jest to możliwe należy używać `let` powiązania w klasie zamiast jawnego pola.</span><span class="sxs-lookup"><span data-stu-id="54a98-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="54a98-144">Pola jawne są przydatne w niektórych scenariuszach współdziałanie, np. gdy są potrzebne do definiowania struktury, który będzie używany w platformie wywołania wywołania do natywnego API ani w zastosowaniach międzyoperacyjnego COM.</span><span class="sxs-lookup"><span data-stu-id="54a98-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="54a98-145">Aby uzyskać więcej informacji, zobacz [funkcji zewnętrznych](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="54a98-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="54a98-146">Innej sytuacji, w którym jawne pole może być konieczne jest podczas pracy z F # generatora kodu który emituje klas bez podstawowego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="54a98-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="54a98-147">Pola jawne są także przydatne zmienne statyczne dla wątku lub podobne konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="54a98-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="54a98-148">Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="54a98-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="54a98-149">Gdy słowa kluczowe `member val` występować razem w definicji typu, jest automatycznie implementowanej właściwości definicji.</span><span class="sxs-lookup"><span data-stu-id="54a98-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="54a98-150">Aby uzyskać więcej informacji, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="54a98-150">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="54a98-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54a98-151">See Also</span></span>
[<span data-ttu-id="54a98-152">Właściwości</span><span class="sxs-lookup"><span data-stu-id="54a98-152">Properties</span></span>](properties.md)

[<span data-ttu-id="54a98-153">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54a98-153">Members</span></span>](index.md)

[<span data-ttu-id="54a98-154">`let` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="54a98-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
