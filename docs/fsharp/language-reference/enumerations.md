---
title: Wyliczenia (F#)
description: 'Dowiedz się, jak używać wyliczenia F # zamiast literały aby kod był bardziej czytelny i łatwy w obsłudze.'
ms.date: 05/16/2016
ms.openlocfilehash: 00faf6e2ad08a7b232a8ae35aa0f7deb1ba3e76a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562995"
---
# <a name="enumerations"></a><span data-ttu-id="e4393-103">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e4393-103">Enumerations</span></span>

<span data-ttu-id="e4393-104">*Wyliczenia*, znanej także jako *wyliczenia*,, są typy całkowite, gdy etykiety są przypisane do podzbioru wartości.</span><span class="sxs-lookup"><span data-stu-id="e4393-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="e4393-105">Można używać ich zamiast literały Aby bardziej czytelny i łatwy w obsłudze kodu.</span><span class="sxs-lookup"><span data-stu-id="e4393-105">You can use them in place of literals to make code more readable and maintainable.</span></span>


## <a name="syntax"></a><span data-ttu-id="e4393-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4393-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="e4393-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4393-107">Remarks</span></span>
<span data-ttu-id="e4393-108">Wyliczenie wygląda podobne jak w przypadku Unii rozłącznej zawierającego wartości prostego, z wyjątkiem tego, czy można określić wartości.</span><span class="sxs-lookup"><span data-stu-id="e4393-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="e4393-109">Wartości są zwykle liczb całkowitych, które są liczone od 0 lub 1 lub liczby całkowite będące pozycji z bitowego.</span><span class="sxs-lookup"><span data-stu-id="e4393-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="e4393-110">Wyliczenie jest przeznaczony do reprezentowania pozycji z bitowego, należy również użyć [flagi](xref:System.FlagsAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e4393-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="e4393-111">Podstawowy typ wyliczenia zależy od literal, która jest używana, tak, aby na przykład można literały z sufiksem, takich jak `1u`, `2u`i tak dalej dla całkowitą bez znaku (`uint32`) typu.</span><span class="sxs-lookup"><span data-stu-id="e4393-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="e4393-112">W przypadku odwoływania się do nazwanych wartości, należy użyć nazwy samego typu wyliczenia jako kwalifikator, czyli `enum-name.value1`, nie tylko `value1`.</span><span class="sxs-lookup"><span data-stu-id="e4393-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="e4393-113">To zachowanie różni się od rozłączne.</span><span class="sxs-lookup"><span data-stu-id="e4393-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="e4393-114">Wynika to z faktu wyliczenia mają zawsze [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e4393-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="e4393-115">Poniższy kod przedstawia deklaracji i korzystania z wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e4393-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="e4393-116">Można z łatwością przekształcić wyliczenia z typem podstawowym za pomocą odpowiednich operatora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="e4393-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="e4393-117">Typy wyliczane może mieć jeden z następujących typów podstawowych: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, i `char`.</span><span class="sxs-lookup"><span data-stu-id="e4393-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="e4393-118">Typy wyliczeniowe są reprezentowane w programie .NET Framework jako typy, które są dziedziczone z `System.Enum`, który z kolei jest dziedziczona `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="e4393-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="e4393-119">W związku z tym są typy wartości, które znajdują się w stos lub tekście obiektu zawierającego, a żadnej wartości Typ podstawowy jest prawidłową wartością wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e4393-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="e4393-120">Jest to znaczące po dopasowania wzorca w wyliczenia wartości, ponieważ musisz podać wzorzec, który przechwytuje wartości bez nazwy.</span><span class="sxs-lookup"><span data-stu-id="e4393-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="e4393-121">`enum` Funkcji w bibliotece języka F # może służyć do generowania wartości wyliczenia, nawet wartość inną niż wstępnie zdefiniowane, nazwane wartości.</span><span class="sxs-lookup"><span data-stu-id="e4393-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="e4393-122">Możesz użyć `enum` działają w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e4393-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="e4393-123">Wartość domyślna `enum` funkcja działa z typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="e4393-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="e4393-124">W związku z tym nie można używać z typów wyliczenia, które mają inne typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="e4393-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="e4393-125">Zamiast tego należy użyć.</span><span class="sxs-lookup"><span data-stu-id="e4393-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a><span data-ttu-id="e4393-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4393-126">See Also</span></span>
[<span data-ttu-id="e4393-127">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="e4393-127">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="e4393-128">Rzutowanie i konwersje</span><span class="sxs-lookup"><span data-stu-id="e4393-128">Casting and Conversions</span></span>](casting-and-conversions.md)
