---
title: Typy pierwotne (F#)
description: 'Poznaj podstawowe typy pierwotne, które są używane w języku F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7832151ee211f56547ecad98fc31f1454cb18870
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="primitive-types"></a><span data-ttu-id="be2c7-103">Typy pierwotne</span><span class="sxs-lookup"><span data-stu-id="be2c7-103">Primitive Types</span></span>

<span data-ttu-id="be2c7-104">Ten temat zawiera podstawowe typy pierwotne, które są używane w języku F #.</span><span class="sxs-lookup"><span data-stu-id="be2c7-104">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="be2c7-105">Dla każdego typu danych umożliwia także odpowiednie typy .NET i wartości minimalną i maksymalną.</span><span class="sxs-lookup"><span data-stu-id="be2c7-105">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="be2c7-106">Podsumowanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="be2c7-106">Summary of Primitive Types</span></span>
<span data-ttu-id="be2c7-107">Poniższa tabela zawiera podsumowanie właściwości pierwotnych typów F #.</span><span class="sxs-lookup"><span data-stu-id="be2c7-107">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="be2c7-108">Typ</span><span class="sxs-lookup"><span data-stu-id="be2c7-108">Type</span></span>|<span data-ttu-id="be2c7-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="be2c7-109">.NET type</span></span>|<span data-ttu-id="be2c7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="be2c7-110">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="be2c7-111">Możliwe wartości to `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="be2c7-111">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="be2c7-112">Wartości z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="be2c7-112">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="be2c7-113">Wartości od -128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="be2c7-113">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="be2c7-114">Wartości od -32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="be2c7-114">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="be2c7-115">Wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="be2c7-115">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="be2c7-116">Wartości od -2,147,483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="be2c7-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="be2c7-117">Wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="be2c7-117">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="be2c7-118">Wartości od-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="be2c7-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="be2c7-119">Wartości z zakresu od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="be2c7-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="be2c7-120">Wskaźnik natywny jako liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="be2c7-120">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="be2c7-121">Wskaźnik natywny jako liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="be2c7-121">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="be2c7-122">Wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="be2c7-122">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="be2c7-123">Tekst Unicode.</span><span class="sxs-lookup"><span data-stu-id="be2c7-123">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="be2c7-124">Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.</span><span class="sxs-lookup"><span data-stu-id="be2c7-124">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="be2c7-125">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="be2c7-125">not applicable</span></span>|<span data-ttu-id="be2c7-126">Wskazuje brak rzeczywistą wartość.</span><span class="sxs-lookup"><span data-stu-id="be2c7-126">Indicates the absence of an actual value.</span></span> <span data-ttu-id="be2c7-127">Typ ma tylko jeden formalny wartość, która jest oznaczona `()`.</span><span class="sxs-lookup"><span data-stu-id="be2c7-127">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="be2c7-128">Wartość jednostki `()`, jest często używana jako symbol zastępczy, gdy wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.</span><span class="sxs-lookup"><span data-stu-id="be2c7-128">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="be2c7-129">Wskazuje nie typem lub wartością.</span><span class="sxs-lookup"><span data-stu-id="be2c7-129">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="be2c7-130">32-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="be2c7-130">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="be2c7-131">64-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="be2c7-131">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="be2c7-132">Można wykonać obliczenia z liczb całkowitych za duża dla typu 64-bitową liczbę całkowitą przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="be2c7-132">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="be2c7-133">`bigint` nie jest uznawany za typ pierwotny; jest skrótem `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="be2c7-133">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="be2c7-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be2c7-134">See Also</span></span>
[<span data-ttu-id="be2c7-135">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="be2c7-135">F# Language Reference</span></span>](index.md)
