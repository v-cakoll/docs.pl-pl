---
title: Wyliczenia
description: Dowiedz się, F# jak używać wyliczeń zamiast literałów, aby kod był bardziej czytelny i konserwowany.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630336"
---
# <a name="enumerations"></a><span data-ttu-id="88395-103">Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="88395-103">Enumerations</span></span>

<span data-ttu-id="88395-104">*Wyliczenia*, znane także jako *wyliczenia*, są typami całkowitymi, w których etykiety są przypisywane do podzestawu wartości.</span><span class="sxs-lookup"><span data-stu-id="88395-104">*Enumerations*, also known as *enums*, , are integral types where labels are assigned to a subset of the values.</span></span> <span data-ttu-id="88395-105">Można ich użyć zamiast literałów, aby kod był bardziej czytelny i możliwy do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="88395-105">You can use them in place of literals to make code more readable and maintainable.</span></span>

## <a name="syntax"></a><span data-ttu-id="88395-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="88395-106">Syntax</span></span>

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a><span data-ttu-id="88395-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88395-107">Remarks</span></span>

<span data-ttu-id="88395-108">Wyliczenie wygląda podobnie jak Unia rozłączna, która ma proste wartości, z tą różnicą, że można określić wartości.</span><span class="sxs-lookup"><span data-stu-id="88395-108">An enumeration looks much like a discriminated union that has simple values, except that the values can be specified.</span></span> <span data-ttu-id="88395-109">Wartości są zwykle liczbami całkowitymi, które zaczynają się od 0 lub 1 lub liczby całkowite reprezentujące pozycje bitowe.</span><span class="sxs-lookup"><span data-stu-id="88395-109">The values are typically integers that start at 0 or 1, or integers that represent bit positions.</span></span> <span data-ttu-id="88395-110">Jeśli Wyliczenie jest przeznaczone do reprezentowania pozycji bitowych, należy również użyć atrybutu flags [](xref:System.FlagsAttribute) .</span><span class="sxs-lookup"><span data-stu-id="88395-110">If an enumeration is intended to represent bit positions, you should also use the [Flags](xref:System.FlagsAttribute) attribute.</span></span>

<span data-ttu-id="88395-111">Typ podstawowy wyliczenia jest określany na podstawie literału, który jest używany, aby na przykład można było użyć literałów z sufiksem, takim jak `1u`, `2u`, i tak dalej, dla typu Liczba całkowita bez znaku (`uint32`).</span><span class="sxs-lookup"><span data-stu-id="88395-111">The underlying type of the enumeration is determined from the literal that is used, so that, for example, you can use literals with a suffix, such as `1u`, `2u`, and so on, for an unsigned integer (`uint32`) type.</span></span>

<span data-ttu-id="88395-112">Gdy odwołujesz się do nazwanych wartości, musisz użyć nazwy typu wyliczenia jako kwalifikatora, czyli `enum-name.value1`nie tylko. `value1`</span><span class="sxs-lookup"><span data-stu-id="88395-112">When you refer to the named values, you must use the name of the enumeration type itself as a qualifier, that is, `enum-name.value1`, not just `value1`.</span></span> <span data-ttu-id="88395-113">To zachowanie różni się od tych związków rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="88395-113">This behavior differs from that of discriminated unions.</span></span> <span data-ttu-id="88395-114">Wynika to z faktu, że wyliczenia mają zawsze atrybut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) .</span><span class="sxs-lookup"><span data-stu-id="88395-114">This is because enumerations always have the [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) attribute.</span></span>

<span data-ttu-id="88395-115">Poniższy kod przedstawia deklarację i użycie wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="88395-115">The following code shows the declaration and use of an enumeration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

<span data-ttu-id="88395-116">Wyliczenia można łatwo przekonwertować na typ podstawowy przy użyciu odpowiedniego operatora, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="88395-116">You can easily convert enumerations to the underlying type by using the appropriate operator, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

<span data-ttu-id="88395-117">Typy wyliczeniowe mogą mieć jeden z następujących typów podstawowych: `sbyte`, `byte`, `int16` `uint16` `uint32` `int32` `uint16`,,,, `int64`, `uint64`,, i `char`.</span><span class="sxs-lookup"><span data-stu-id="88395-117">Enumerated types can have one of the following underlying types: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, and `char`.</span></span> <span data-ttu-id="88395-118">Typy wyliczeniowe są reprezentowane w .NET Framework jako typy dziedziczone z `System.Enum`, które z kolei są dziedziczone z. `System.ValueType`</span><span class="sxs-lookup"><span data-stu-id="88395-118">Enumeration types are represented in the .NET Framework as types that are inherited from `System.Enum`, which in turn is inherited from `System.ValueType`.</span></span> <span data-ttu-id="88395-119">Z tego względu są to typy wartości, które znajdują się na stosie lub są wbudowane w obiekt zawierający, a każda wartość typu podstawowego jest prawidłową wartością wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="88395-119">Thus, they are value types that are located on the stack or inline in the containing object, and any value of the underlying type is a valid value of the enumeration.</span></span> <span data-ttu-id="88395-120">Jest to istotne w przypadku dopasowania wzorców do wartości wyliczenia, ponieważ należy dostarczyć wzorzec, który przechwytuje wartości nienazwanych.</span><span class="sxs-lookup"><span data-stu-id="88395-120">This is significant when pattern matching on enumeration values, because you have to provide a pattern that catches the unnamed values.</span></span>

<span data-ttu-id="88395-121">Funkcja w F# bibliotece może służyć do generowania wartości wyliczenia, nawet wartości innej niż jedna ze wstępnie zdefiniowanych wartości nazwanych. `enum`</span><span class="sxs-lookup"><span data-stu-id="88395-121">The `enum` function in the F# library can be used to generate an enumeration value, even a value other than one of the predefined, named values.</span></span> <span data-ttu-id="88395-122">`enum` Używasz funkcji w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="88395-122">You use the `enum` function as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

<span data-ttu-id="88395-123">Funkcja Domyślna `enum` działa z typem `int32`.</span><span class="sxs-lookup"><span data-stu-id="88395-123">The default `enum` function works with type `int32`.</span></span> <span data-ttu-id="88395-124">W związku z tym nie można jej używać z typami wyliczeniowymi, które mają inne typy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="88395-124">Therefore, it cannot be used with enumeration types that have other underlying types.</span></span> <span data-ttu-id="88395-125">Zamiast tego należy użyć poniższego polecenia.</span><span class="sxs-lookup"><span data-stu-id="88395-125">Instead, use the following.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

<span data-ttu-id="88395-126">Ponadto przypadki wyliczeniowe są zawsze emitowane jako `public`.</span><span class="sxs-lookup"><span data-stu-id="88395-126">Additionally, cases for enums are always emitted as `public`.</span></span> <span data-ttu-id="88395-127">Jest to tak, aby były wyrównane C# z i resztą platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="88395-127">This is so that they align with C# and the rest of the .NET platform.</span></span>

## <a name="see-also"></a><span data-ttu-id="88395-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88395-128">See also</span></span>

- [<span data-ttu-id="88395-129">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="88395-129">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="88395-130">Rzutowanie i konwersje</span><span class="sxs-lookup"><span data-stu-id="88395-130">Casting and Conversions</span></span>](casting-and-conversions.md)
