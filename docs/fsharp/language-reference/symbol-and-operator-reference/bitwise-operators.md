---
title: Operatory bitowe (F#)
description: 'Więcej informacji na temat operatory bitowe, które są dostępne w języku programowania w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4d5abff564a5d1dcbe52b99edf431ca10e442061
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="bitwise-operators"></a><span data-ttu-id="94064-103">Operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="94064-103">Bitwise Operators</span></span>

<span data-ttu-id="94064-104">W tym temacie opisano operatory bitowe, które są dostępne w języku F #.</span><span class="sxs-lookup"><span data-stu-id="94064-104">This topic describes bitwise operators that are available in the F# language.</span></span>

## <a name="summary-of-bitwise-operators"></a><span data-ttu-id="94064-105">Podsumowanie operatory bitowe</span><span class="sxs-lookup"><span data-stu-id="94064-105">Summary of Bitwise Operators</span></span>
<span data-ttu-id="94064-106">W poniższej tabeli opisano operatory bitowe, które są obsługiwane w przypadku rozpakowany typy całkowite w języku F #.</span><span class="sxs-lookup"><span data-stu-id="94064-106">The following table describes the bitwise operators that are supported for unboxed integral types in the F# language.</span></span>

|<span data-ttu-id="94064-107">Operator</span><span class="sxs-lookup"><span data-stu-id="94064-107">Operator</span></span>|<span data-ttu-id="94064-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94064-108">Notes</span></span>|
|--------|-----|
|`&&&`|<span data-ttu-id="94064-109">Bitowy operator AND.</span><span class="sxs-lookup"><span data-stu-id="94064-109">Bitwise AND operator.</span></span> <span data-ttu-id="94064-110">Usługa BITS w wyniku ma wartość 1, tylko wtedy, gdy odpowiednich bitów w obu źródłowe argumenty operacji są 1.</span><span class="sxs-lookup"><span data-stu-id="94064-110">Bits in the result have the value 1 if and only if the corresponding bits in both source operands are 1.</span></span>|
|<code>&#124;&#124;&#124;</code>|<span data-ttu-id="94064-111">Bitowy operator OR.</span><span class="sxs-lookup"><span data-stu-id="94064-111">Bitwise OR operator.</span></span> <span data-ttu-id="94064-112">Usługi BITS w wyniku ma wartość 1, jeśli dowolny z odpowiednich bitów w źródle argumenty operacji są 1.</span><span class="sxs-lookup"><span data-stu-id="94064-112">Bits in the result have the value 1 if either of the corresponding bits in the source operands are 1.</span></span>|
|`^^^`|<span data-ttu-id="94064-113">Operator wyłączny operator OR.</span><span class="sxs-lookup"><span data-stu-id="94064-113">Bitwise exclusive OR operator.</span></span> <span data-ttu-id="94064-114">Usługi BITS w wyniku ma wartość 1, tylko wtedy, gdy w źródłowe argumenty operacji mają nierówne wartości.</span><span class="sxs-lookup"><span data-stu-id="94064-114">Bits in the result have the value 1 if and only if bits in the source operands have unequal values.</span></span>|
|`~~~`|<span data-ttu-id="94064-115">Operator negacji bitowej.</span><span class="sxs-lookup"><span data-stu-id="94064-115">Bitwise negation operator.</span></span> <span data-ttu-id="94064-116">To jest operatora jednoargumentowego i zwraca wynik, w którym wszystkie bity 0 w operandu źródła są konwertowane na bitów 1 i wszystkie bity 1 są konwertowane na bitów 0.</span><span class="sxs-lookup"><span data-stu-id="94064-116">This is a unary operator and produces a result in which all 0 bits in the source operand are converted to 1 bits and all 1 bits are converted to 0 bits.</span></span>|
|`<<<`|<span data-ttu-id="94064-117">Bitowy operator przesunięcia w lewo.</span><span class="sxs-lookup"><span data-stu-id="94064-117">Bitwise left-shift operator.</span></span> <span data-ttu-id="94064-118">Wynik jest pierwszy argument operacji z bitami przesunięte liczbę bitów w drugi argument operacji po lewej.</span><span class="sxs-lookup"><span data-stu-id="94064-118">The result is the first operand with bits shifted left by the number of bits in the second operand.</span></span> <span data-ttu-id="94064-119">Bity przesunąć poza najbardziej znaczących pozycji nie są obracane do najmniej znaczący pozycji.</span><span class="sxs-lookup"><span data-stu-id="94064-119">Bits shifted off the most significant position are not rotated into the least significant position.</span></span> <span data-ttu-id="94064-120">Najmniej znaczących bitów jest uzupełniana zerami z.</span><span class="sxs-lookup"><span data-stu-id="94064-120">The least significant bits are padded with zeros.</span></span> <span data-ttu-id="94064-121">Typ drugiego argumentu jest `int32`.</span><span class="sxs-lookup"><span data-stu-id="94064-121">The type of the second argument is `int32`.</span></span>|
|`>>>`|<span data-ttu-id="94064-122">Bitowy operator przesunięcia w prawo.</span><span class="sxs-lookup"><span data-stu-id="94064-122">Bitwise right-shift operator.</span></span> <span data-ttu-id="94064-123">Wynik jest pierwszym argumentem z bitami przesunięte liczbę bitów w drugi argument operacji po prawej.</span><span class="sxs-lookup"><span data-stu-id="94064-123">The result is the first operand with bits shifted right by the number of bits in the second operand.</span></span> <span data-ttu-id="94064-124">Bity przesunąć poza najmniej znaczący pozycji nie są obracane do najważniejszych pozycji.</span><span class="sxs-lookup"><span data-stu-id="94064-124">Bits shifted off the least significant position are not rotated into the most significant position.</span></span> <span data-ttu-id="94064-125">Typy bez znaku, aby uzyskać najbardziej znaczących bitów jest uzupełniana zerami z.</span><span class="sxs-lookup"><span data-stu-id="94064-125">For unsigned types, the most significant bits are padded with zeros.</span></span> <span data-ttu-id="94064-126">Typy ze znakiem, aby uzyskać najbardziej znaczących bitów są dopełniane przy tych.</span><span class="sxs-lookup"><span data-stu-id="94064-126">For signed types, the most significant bits are padded with ones.</span></span> <span data-ttu-id="94064-127">Typ drugiego argumentu jest `int32`.</span><span class="sxs-lookup"><span data-stu-id="94064-127">The type of the second argument is `int32`.</span></span>|

<span data-ttu-id="94064-128">Następujące typy mogą być używane z bitowego operatory: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, i `unativeint`.</span><span class="sxs-lookup"><span data-stu-id="94064-128">The following types can be used with bitwise operators: `byte`, `sbyte`, `int16`, `uint16`, `int32 (int)`, `uint32`, `int64`, `uint64`, `nativeint`, and `unativeint`.</span></span>

## <a name="see-also"></a><span data-ttu-id="94064-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94064-129">See Also</span></span>
[<span data-ttu-id="94064-130">Odwołanie do symboli i operatorów</span><span class="sxs-lookup"><span data-stu-id="94064-130">Symbol and Operator Reference</span></span>](index.md)

[<span data-ttu-id="94064-131">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="94064-131">Arithmetic Operators</span></span>](arithmetic-operators.md)

[<span data-ttu-id="94064-132">Operatory logiczne</span><span class="sxs-lookup"><span data-stu-id="94064-132">Boolean Operators</span></span>](boolean-operators.md)

