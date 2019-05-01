---
title: Wyliczenia
description: Dowiedz się, jak używać F# wyliczeń zamiast literałów sprawić, że kod bardziej czytelny i łatwy w obsłudze.
ms.date: 05/16/2016
ms.openlocfilehash: a8839b73de074f62606b70ffe969a53b3db753bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921579"
---
# <a name="enumerations"></a><span data-ttu-id="5d646-103">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5d646-103">Enumerations</span></span>

<span data-ttu-id="5d646-104">*Wyliczenia*, znane również jako *wyliczenia*,, są typami całkowitymi, gdy etykiety są przypisane do podzbioru wartości.</span><span class="sxs-lookup"><span data-stu-id="5d646-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="5d646-105">Można je zamiast literałów wprowadzić kod bardziej czytelny i łatwy w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="5d646-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="5d646-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d646-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="5d646-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d646-107">Remarks</span></span>

<span data-ttu-id="5d646-108">Wyliczenie wygląda bardzo podobnie złożeniem dyskryminowanym, które ma prostych wartości, z tą różnicą, że można określić wartości.</span><span class="sxs-lookup"><span data-stu-id="5d646-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="5d646-109">Wartości są zwykle liczb całkowitych, które rozpoczynają się od 0 lub 1 lub liczb całkowitych reprezentujących pozycji bitów.</span><span class="sxs-lookup"><span data-stu-id="5d646-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="5d646-110">Jeśli wyliczenie jest przeznaczony do reprezentowania pozycje bitów, należy również użyć [flagi](xref:System.FlagsAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5d646-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="5d646-111">Podstawowym typem wyliczenia jest określana na podstawie literał, która jest używana, tak aby na przykład można literały z sufiksu, takich jak `1u`, `2u`i tak dalej na liczbę całkowitą bez znaku (`uint32`) typu.</span><span class="sxs-lookup"><span data-stu-id="5d646-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="5d646-112">W przypadku nazwanych wartości, należy użyć nazwy samego typu wyliczenia jako kwalifikator, oznacza to, `enum-name.value1`, nie tylko `value1`.</span><span class="sxs-lookup"><span data-stu-id="5d646-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="5d646-113">To zachowanie różni się od sumy rozłączne.</span><span class="sxs-lookup"><span data-stu-id="5d646-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="5d646-114">Jest to spowodowane wyliczenia zawsze mają [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5d646-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="5d646-115">Poniższy kod ilustruje deklarowanie i używanie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5d646-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="5d646-116">Można z łatwością przekształcić wyliczenia typem podstawowym za pomocą odpowiedniego operatora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5d646-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="5d646-117">Typy wyliczone może mieć jedną z następujących typów podstawowych: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, i `char`.</span><span class="sxs-lookup"><span data-stu-id="5d646-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="5d646-118">Typy wyliczeniowe są reprezentowane w .NET Framework jako typy, które są dziedziczone z `System.Enum`, który z kolei jest odziedziczone po `System.ValueType`.</span><span class="sxs-lookup"><span data-stu-id="5d646-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="5d646-119">Dlatego są typy wartości, które znajdują się w stos lub bezpośrednio w zawierającego go obiektu i dowolną wartość typu podstawowego jest prawidłową wartością wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5d646-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="5d646-120">Jest to znaczące podczas dopasowania do wzorca w wyliczenia wartości, ponieważ musisz podać wzorzec, który przechwytuje nienazwanych wartości.</span><span class="sxs-lookup"><span data-stu-id="5d646-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="5d646-121">`enum` Działa w programach F# biblioteki może służyć do generowania wartości wyliczenia, nawet wartość inna niż jeden z wstępnie zdefiniowanych, o nazwie wartości.</span><span class="sxs-lookup"><span data-stu-id="5d646-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="5d646-122">Możesz użyć `enum` funkcji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="5d646-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="5d646-123">Wartość domyślna `enum` funkcja działa z typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="5d646-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="5d646-124">W związku z tym nie można używać z typami wyliczenia, które mają innych typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="5d646-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="5d646-125">Zamiast tego należy użyć.</span><span class="sxs-lookup"><span data-stu-id="5d646-125">Instead, use the following.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="5d646-126">Ponadto przypadków dla typów wyliczeniowych zawsze są emitowane jako `public`.</span><span class="sxs-lookup"><span data-stu-id="5d646-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="5d646-127">Jest to tak, aby były wyrównane w języku C# i pozostałą część platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="5d646-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d646-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d646-128">See also</span></span>

- [<span data-ttu-id="5d646-129">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="5d646-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5d646-130">Rzutowanie i konwersje</span><span class="sxs-lookup"><span data-stu-id="5d646-130">Casting and Conversions</span></span>](casting-and-conversions.md)