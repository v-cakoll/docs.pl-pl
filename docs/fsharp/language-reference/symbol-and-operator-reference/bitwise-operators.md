---
title: Operatory bitowe (F#)
description: "Więcej informacji na temat operatory bitowe, które są dostępne w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8a2c87f5-b4c7-47fe-8580-82c956f605e5
ms.openlocfilehash: 61a8e6bafe97a229480c967a4afb5d2a256474c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-operators"></a><span data-ttu-id="7bda4-104">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="7bda4-104">Bitwise Operators</span></span>

<span data-ttu-id="7bda4-105">W tym temacie opisano operatory bitowe, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="7bda4-105">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="7bda4-106">Podsumowanie operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="7bda4-106">Summary of Bitwise Operators</span></span>
<span data-ttu-id="7bda4-107">W poniższej tabeli opisano operatory bitowe, które są obsługiwane w przypadku rozpakowany typy całkowite w języku F #.</span><span class="sxs-lookup"><span data-stu-id="7bda4-107">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="7bda4-108">Operator</span><span class="sxs-lookup"><span data-stu-id="7bda4-108">Operator</span></span>|<span data-ttu-id="7bda4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bda4-109">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="7bda4-110">Bitowy operator AND.</span><span class="sxs-lookup"><span data-stu-id="7bda4-110">Bitwise AND operator.</span></span> <span data-ttu-id="7bda4-111">Usługa BITS w wyniku ma wartość 1, tylko wtedy, gdy odpowiednich bitów w obu źródłowe argumenty operacji są 1.</span><span class="sxs-lookup"><span data-stu-id="7bda4-111">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="7bda4-112">Bitowy operator OR.</span><span class="sxs-lookup"><span data-stu-id="7bda4-112">Bitwise OR operator.</span></span> <span data-ttu-id="7bda4-113">Usługi BITS w wyniku ma wartość 1, jeśli dowolny z odpowiednich bitów w źródle argumenty operacji są 1.</span><span class="sxs-lookup"><span data-stu-id="7bda4-113">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="7bda4-114">Operator wyłączny operator OR.</span><span class="sxs-lookup"><span data-stu-id="7bda4-114">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="7bda4-115">Usługi BITS w wyniku ma wartość 1, tylko wtedy, gdy w źródłowe argumenty operacji mają nierówne wartości.</span><span class="sxs-lookup"><span data-stu-id="7bda4-115">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="7bda4-116">Operator negacji bitowej.</span><span class="sxs-lookup"><span data-stu-id="7bda4-116">Bitwise negation operator.</span></span> <span data-ttu-id="7bda4-117">To jest operatora jednoargumentowego i zwraca wynik, w którym wszystkie bity 0 w operandu źródła są konwertowane na bitów 1 i wszystkie bity 1 są konwertowane na bitów 0.</span><span class="sxs-lookup"><span data-stu-id="7bda4-117">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="7bda4-118">Bitowy operator przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="7bda4-118">Bitwise left-shift operator.</span></span> <span data-ttu-id="7bda4-119">Wynik jest pierwszy argument operacji z bitami przesunięte liczbę bitów w drugi argument operacji po lewej.</span><span class="sxs-lookup"><span data-stu-id="7bda4-119">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="7bda4-120">Bity przesunąć poza najbardziej znaczących pozycji nie są obracane do najmniej znaczący pozycji.</span><span class="sxs-lookup"><span data-stu-id="7bda4-120">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="7bda4-121">Najmniej znaczących bitów jest uzupełniana zerami z.</span><span class="sxs-lookup"><span data-stu-id="7bda4-121">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="7bda4-122">Typ drugiego argumentu jest `int32`.</span><span class="sxs-lookup"><span data-stu-id="7bda4-122">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="7bda4-123">Bitowy operator przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="7bda4-123">Bitwise right-shift operator.</span></span> <span data-ttu-id="7bda4-124">Wynik jest pierwszym argumentem z bitami przesunięte liczbę bitów w drugi argument operacji po prawej.</span><span class="sxs-lookup"><span data-stu-id="7bda4-124">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="7bda4-125">Bity przesunąć poza najmniej znaczący pozycji nie są obracane do najważniejszych pozycji.</span><span class="sxs-lookup"><span data-stu-id="7bda4-125">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="7bda4-126">Typy bez znaku, aby uzyskać najbardziej znaczących bitów jest uzupełniana zerami z.</span><span class="sxs-lookup"><span data-stu-id="7bda4-126">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="7bda4-127">Typy ze znakiem, aby uzyskać najbardziej znaczących bitów są dopełniane przy tych.</span><span class="sxs-lookup"><span data-stu-id="7bda4-127">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="7bda4-128">Typ drugiego argumentu jest `int32`.</span><span class="sxs-lookup"><span data-stu-id="7bda4-128">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="7bda4-129">Następujące typy mogą być używane z bitowego operatory: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, i `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="7bda4-129">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bda4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bda4-130">See Also</span></span>
[<span data-ttu-id="7bda4-131">Operator odwołanie do symbolu i</span><span class="sxs-lookup"><span data-stu-id="7bda4-131">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="7bda4-132">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="7bda4-132">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="7bda4-133">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="7bda4-133">Boolean Operators</span></span>](boolean-operators.md)

