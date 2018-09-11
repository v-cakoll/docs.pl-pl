---
title: 'Pola jawne: val — Słowo kluczowe (F#)'
description: 'Więcej informacji na temat języka F # "val" słowo kluczowe, które jest używane do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez inicjowania typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 9cd06f7e90192be79490dd0ff67f118cce4339c3
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262467"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="00b8b-103">Pola jawne: val — Słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="00b8b-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="00b8b-104">`val` — Słowo kluczowe jest używane do deklarowania lokalizację do przechowywania wartości w typie klasy lub struktury, bez jego inicjowania.</span><span class="sxs-lookup"><span data-stu-id="00b8b-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="00b8b-105">Lokalizacje przechowywania, zadeklarowany w ten sposób są nazywane *pola jawne*.</span><span class="sxs-lookup"><span data-stu-id="00b8b-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="00b8b-106">Używanie innego `val` — słowo kluczowe jest używana razem z `member` — słowo kluczowe do deklarowania automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="00b8b-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="00b8b-107">Aby uzyskać więcej informacji dotyczących automatycznie implementowanych właściwości, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="00b8b-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="00b8b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="00b8b-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="00b8b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00b8b-109">Remarks</span></span>

<span data-ttu-id="00b8b-110">Zwykle sposobem zdefiniowania pola w typie klasy lub struktury jest użycie `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="00b8b-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="00b8b-111">Jednak `let` powiązania musi zostać zainicjowany jako część konstruktora klasy, które nie zawsze jest możliwe, wymagane lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="00b8b-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="00b8b-112">Możesz użyć `val` — słowo kluczowe, jeśli chcesz, aby pola, które nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="00b8b-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="00b8b-113">Pola jawne może być statyczne lub niestatycznych.</span><span class="sxs-lookup"><span data-stu-id="00b8b-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="00b8b-114">*Modyfikator dostępu* może być `public`, `private`, lub `internal`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="00b8b-115">Pola jawne są domyślnie publiczne.</span><span class="sxs-lookup"><span data-stu-id="00b8b-115">By default, explicit fields are public.</span></span> <span data-ttu-id="00b8b-116">To różni się od `let` powiązania w klasach, które są zawsze prywatne.</span><span class="sxs-lookup"><span data-stu-id="00b8b-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="00b8b-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atrybut jest wymagany na jawne pól w typach klasy, które mają podstawowy Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="00b8b-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="00b8b-118">Ten atrybut określa, że pole jest inicjowane od zera.</span><span class="sxs-lookup"><span data-stu-id="00b8b-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="00b8b-119">Typ pola musi obsługiwać inicjowanie zero.</span><span class="sxs-lookup"><span data-stu-id="00b8b-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="00b8b-120">Typ obsługuje inicjowania zero, jeśli jest to jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="00b8b-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="00b8b-121">Pierwotny typ, który ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="00b8b-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="00b8b-122">Typ, który obsługuje wartości null, albo jako wartość normalna, jako wartość nietypowe lub jako reprezentację wartości.</span><span class="sxs-lookup"><span data-stu-id="00b8b-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="00b8b-123">Obejmuje to klasy, krotek, rekordy, funkcje, interfejsy, typy odwołań platformy .NET, `unit` typu i dyskryminowanego typu złożenia.</span><span class="sxs-lookup"><span data-stu-id="00b8b-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="00b8b-124">Typ wartości platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="00b8b-124">A .NET value type.</span></span>

- <span data-ttu-id="00b8b-125">Struktura, w których wszystkie pola obsługuje domyślną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="00b8b-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="00b8b-126">Na przykład niezmienne pole o nazwie `someField` został skompilowany polem zapasowym na platformie .NET reprezentacji o nazwie `someField@`, i możesz uzyskać dostęp do wartości przechowywanej za pomocą właściwości o nazwie `someField`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="00b8b-127">Modyfikowalne pola reprezentacja .NET skompilowanych jest polem .NET.</span><span class="sxs-lookup"><span data-stu-id="00b8b-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
<span data-ttu-id="00b8b-128">`Note` Przestrzeń nazw .NET Framework `System.ComponentModel` zawiera atrybut, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="00b8b-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="00b8b-129">Aby uzyskać informacji na temat tego atrybutu, zobacz `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="00b8b-130">Poniższy kod przedstawia użycie pola jawne i dla porównania `let` powiązania w klasie, która ma konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="00b8b-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="00b8b-131">Należy pamiętać, że `let`— pole związane `myInt1` jest prywatny.</span><span class="sxs-lookup"><span data-stu-id="00b8b-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="00b8b-132">Gdy `let`— pola związanego `myInt1` jest wywoływany przez metodę elementu członkowskiego własny identyfikator `this` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="00b8b-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="00b8b-133">Jednak gdy odwołujesz się do pola jawne `myInt2` i `myString`, własny identyfikator jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="00b8b-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="00b8b-134">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="00b8b-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="00b8b-135">Poniższy kod przedstawia użycie pola jawne w klasie, która nie ma konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="00b8b-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="00b8b-136">W tym przypadku `DefaultValue` atrybut nie jest wymagana, ale wszystkie pola muszą być zainicjowane w konstruktorach, które są zdefiniowane dla typu.</span><span class="sxs-lookup"><span data-stu-id="00b8b-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="00b8b-137">Dane wyjściowe są `35 22`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-137">The output is `35 22`.</span></span>

<span data-ttu-id="00b8b-138">Poniższy kod przedstawia użycie pola jawne w strukturze.</span><span class="sxs-lookup"><span data-stu-id="00b8b-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="00b8b-139">Ponieważ struktura jest typem wartości, automatycznie ma domyślnego konstruktora, która ustawia wartości pól do zera.</span><span class="sxs-lookup"><span data-stu-id="00b8b-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="00b8b-140">W związku z tym `DefaultValue` atrybut nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="00b8b-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="00b8b-141">Dane wyjściowe są `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="00b8b-142">Pola jawne nie są przeznaczone do użytku procedur.</span><span class="sxs-lookup"><span data-stu-id="00b8b-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="00b8b-143">Ogólnie rzecz biorąc, gdy jest to możliwe należy używać `let` powiązania w klasie zamiast jawnego pola.</span><span class="sxs-lookup"><span data-stu-id="00b8b-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="00b8b-144">Pola jawne są przydatne w niektórych scenariuszach współpracy, takie jak kiedy należy zdefiniować strukturę, która będzie używana w wywołaniu do natywnych interfejsów API lub w scenariuszach międzyoperacyjnego modelu COM wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="00b8b-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="00b8b-145">Aby uzyskać więcej informacji, zobacz [funkcji zewnętrznych](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="00b8b-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="00b8b-146">Innej sytuacji, w którym może być konieczne jawne pola jest podczas pracy z F # generatora kodu, który emituje klasy bez konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="00b8b-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="00b8b-147">Pola jawne są także przydatne zmienne statyczne wątku lub podobne konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="00b8b-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="00b8b-148">Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="00b8b-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="00b8b-149">Gdy słowa kluczowe `member val` pojawiają się razem w definicji typu, jest on definicją automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="00b8b-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="00b8b-150">Aby uzyskać więcej informacji, zobacz [właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="00b8b-150">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="00b8b-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00b8b-151">See also</span></span>

- [<span data-ttu-id="00b8b-152">Właściwości</span><span class="sxs-lookup"><span data-stu-id="00b8b-152">Properties</span></span>](properties.md)
- [<span data-ttu-id="00b8b-153">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="00b8b-153">Members</span></span>](index.md)
- [<span data-ttu-id="00b8b-154">`let` Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="00b8b-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
