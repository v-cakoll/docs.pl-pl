---
title: 'Pola jawne: Val — słowo kluczowe'
description: Dowiedz się F# więcej o słowie kluczowym "Val", które jest używane do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury bez inicjalizacji typu.
ms.date: 05/16/2016
ms.openlocfilehash: 13e0ba2875e8accfd1c0da0e1c6fef4973309f9b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627534"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="8667f-103">Pola jawne: Val — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="8667f-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="8667f-104">`val` Słowo kluczowe jest używane do deklarowania lokalizacji do przechowywania wartości w typie klasy lub struktury, bez jej inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="8667f-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="8667f-105">Lokalizacje magazynu zadeklarowane w ten sposób są nazywane *jawnymi polami*.</span><span class="sxs-lookup"><span data-stu-id="8667f-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="8667f-106">Inne użycie `val` słowa kluczowego jest w połączeniu `member` ze słowem kluczowym w celu zadeklarować właściwości, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="8667f-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="8667f-107">Aby uzyskać więcej informacji na temat właściwości, które są implementowane, zobacz [Właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="8667f-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="8667f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8667f-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="8667f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8667f-109">Remarks</span></span>

<span data-ttu-id="8667f-110">Typowym sposobem definiowania pól w klasie lub typie struktury jest użycie `let` powiązania.</span><span class="sxs-lookup"><span data-stu-id="8667f-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="8667f-111">`let` Jednakże powiązania muszą być zainicjowane jako część konstruktora klasy, co nie zawsze jest możliwe, konieczne lub pożądane.</span><span class="sxs-lookup"><span data-stu-id="8667f-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="8667f-112">Możesz użyć `val` słowa kluczowego, gdy chcesz, aby pole, które jest niezainicjowane.</span><span class="sxs-lookup"><span data-stu-id="8667f-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="8667f-113">Jawne pola mogą być statyczne lub niestatyczne.</span><span class="sxs-lookup"><span data-stu-id="8667f-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="8667f-114">*Modyfikatorem dostępu* może być `public`, `private`, lub `internal`.</span><span class="sxs-lookup"><span data-stu-id="8667f-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="8667f-115">Domyślnie jawne pola są publiczne.</span><span class="sxs-lookup"><span data-stu-id="8667f-115">By default, explicit fields are public.</span></span> <span data-ttu-id="8667f-116">Różni się to `let` od powiązań w klasach, które są zawsze prywatne.</span><span class="sxs-lookup"><span data-stu-id="8667f-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="8667f-117">Atrybut [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) jest wymagany w jawnych polach w typach klas, które mają Konstruktor podstawowy.</span><span class="sxs-lookup"><span data-stu-id="8667f-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="8667f-118">Ten atrybut określa, że pole jest inicjowane na wartość zero.</span><span class="sxs-lookup"><span data-stu-id="8667f-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="8667f-119">Typ pola musi obsługiwać inicjowanie o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="8667f-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="8667f-120">Typ obsługuje Inicjowanie zero, jeśli jest jedną z następujących:</span><span class="sxs-lookup"><span data-stu-id="8667f-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="8667f-121">Typ pierwotny, który ma wartość zerową.</span><span class="sxs-lookup"><span data-stu-id="8667f-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="8667f-122">Typ, który obsługuje wartość null, jako wartość normalną, jako wartość nietypową lub jako reprezentację wartości.</span><span class="sxs-lookup"><span data-stu-id="8667f-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="8667f-123">Obejmuje to klasy, krotki, rekordy, funkcje, interfejsy, typy odwołań platformy .NET, `unit` typ i typy Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="8667f-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="8667f-124">Typ wartości .NET.</span><span class="sxs-lookup"><span data-stu-id="8667f-124">A .NET value type.</span></span>

- <span data-ttu-id="8667f-125">Struktura, której pola wszystkie obsługują domyślną wartość zerową.</span><span class="sxs-lookup"><span data-stu-id="8667f-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="8667f-126">Na przykład niezmienne pole o nazwie `someField` ma pole zapasowe w skompilowanej reprezentacji .NET o nazwie `someField@`i uzyskuje dostęp do przechowywanej wartości przy użyciu właściwości `someField`o nazwie.</span><span class="sxs-lookup"><span data-stu-id="8667f-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="8667f-127">W przypadku pola modyfikowalnego skompilowana reprezentacja .NET jest polem platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="8667f-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
><span data-ttu-id="8667f-128">Przestrzeń nazw `System.ComponentModel` .NET Framework zawiera atrybut, który ma taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="8667f-128">The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="8667f-129">Informacje o tym atrybucie można znaleźć w `System.ComponentModel.DefaultValueAttribute`temacie.</span><span class="sxs-lookup"><span data-stu-id="8667f-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="8667f-130">Poniższy kod przedstawia użycie jawnych pól i, w przypadku porównania, `let` powiązanie w klasie, która ma Konstruktor podstawowy.</span><span class="sxs-lookup"><span data-stu-id="8667f-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="8667f-131">Zwróć uwagę, `let`że pole `myInt1` -powiązane jest prywatne.</span><span class="sxs-lookup"><span data-stu-id="8667f-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="8667f-132">Gdy odwołanie do pola `myInt1` jest powiązane z metody składowej, jego identyfikator `this` samodzielny nie jest wymagany. `let`</span><span class="sxs-lookup"><span data-stu-id="8667f-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="8667f-133">Ale w przypadku odwoływania się do jawnych `myString`pól `myInt2` i, wymagany jest sam identyfikator.</span><span class="sxs-lookup"><span data-stu-id="8667f-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="8667f-134">Wynik jest następujący:</span><span class="sxs-lookup"><span data-stu-id="8667f-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="8667f-135">Poniższy kod przedstawia użycie jawnych pól w klasie, która nie ma konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8667f-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="8667f-136">W tym przypadku `DefaultValue` atrybut nie jest wymagany, ale wszystkie pola muszą być zainicjowane w konstruktorach, które są zdefiniowane dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="8667f-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="8667f-137">Dane wyjściowe to `35 22`.</span><span class="sxs-lookup"><span data-stu-id="8667f-137">The output is `35 22`.</span></span>

<span data-ttu-id="8667f-138">Poniższy kod przedstawia użycie jawnych pól w strukturze.</span><span class="sxs-lookup"><span data-stu-id="8667f-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="8667f-139">Ponieważ struktura jest typem wartości, automatycznie ma konstruktora domyślnego, który ustawia wartości pól na zero.</span><span class="sxs-lookup"><span data-stu-id="8667f-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="8667f-140">W związku z `DefaultValue` tym atrybut nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8667f-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="8667f-141">Dane wyjściowe to `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="8667f-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="8667f-142">**Uważaj**, jeśli zamierzasz zainicjować strukturę przy użyciu `mutable` pól bez `mutable` słowa kluczowego, przypisania będą działać na kopii struktury, która zostanie odrzucona po przypisaniu.</span><span class="sxs-lookup"><span data-stu-id="8667f-142">**Beware**, if you are going to initialize your structure with `mutable` fields without `mutable` keyword, your assignments will work on a copy of the structure which will be discarded right after assignment.</span></span> <span data-ttu-id="8667f-143">W związku z tym struktura nie ulegnie zmianie.</span><span class="sxs-lookup"><span data-stu-id="8667f-143">Therefore your structure won't change.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

<span data-ttu-id="8667f-144">Jawne pola nie są przeznaczone do rutynowego użycia.</span><span class="sxs-lookup"><span data-stu-id="8667f-144">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="8667f-145">Ogólnie rzecz biorąc, gdy jest to możliwe, `let` należy użyć powiązania w klasie zamiast pola jawnego.</span><span class="sxs-lookup"><span data-stu-id="8667f-145">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="8667f-146">Jawne pola są przydatne w niektórych scenariuszach współdziałania, na przykład w sytuacji, gdy trzeba zdefiniować strukturę, która będzie używana w wywołaniu wywołania platformy do natywnego interfejsu API lub w scenariuszach międzyoperacyjnych modelu COM.</span><span class="sxs-lookup"><span data-stu-id="8667f-146">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="8667f-147">Aby uzyskać więcej informacji, zobacz [funkcje zewnętrzne](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="8667f-147">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="8667f-148">Inną sytuacją, w której może być wymagane jawne pole, jest to, że podczas F# pracy z generatorem kodu, który emituje klasy bez konstruktora podstawowego.</span><span class="sxs-lookup"><span data-stu-id="8667f-148">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="8667f-149">Jawne pola są również przydatne w przypadku zmiennych statycznych wątków lub podobnych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="8667f-149">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="8667f-150">Aby uzyskać więcej informacji, zobacz `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8667f-150">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="8667f-151">Gdy słowa kluczowe `member val` są wyświetlane razem w definicji typu, jest to definicja automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8667f-151">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="8667f-152">Aby uzyskać więcej informacji, zobacz [Właściwości](properties.md).</span><span class="sxs-lookup"><span data-stu-id="8667f-152">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8667f-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8667f-153">See also</span></span>

- [<span data-ttu-id="8667f-154">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8667f-154">Properties</span></span>](properties.md)
- [<span data-ttu-id="8667f-155">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8667f-155">Members</span></span>](index.md)
- [<span data-ttu-id="8667f-156">`let`Powiązania w klasach</span><span class="sxs-lookup"><span data-stu-id="8667f-156">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
