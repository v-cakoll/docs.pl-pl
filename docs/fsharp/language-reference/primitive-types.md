---
title: Typy pierwotne (F#)
description: 'Poznaj podstawowe typy pierwotne, które są używane w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: efe419e5ebf2e49be9433bbd3025ff290d648296
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="primitive-types"></a><span data-ttu-id="53516-103">Typy pierwotne</span><span class="sxs-lookup"><span data-stu-id="53516-103">Primitive Types</span></span>

<span data-ttu-id="53516-104">Ten temat zawiera podstawowe typy pierwotne, które są używane w języku F #.</span><span class="sxs-lookup"><span data-stu-id="53516-104">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="53516-105">Dla każdego typu danych umożliwia także odpowiednie typy .NET i wartości minimalną i maksymalną.</span><span class="sxs-lookup"><span data-stu-id="53516-105">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="53516-106">Podsumowanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="53516-106">Summary of Primitive Types</span></span>
<span data-ttu-id="53516-107">Poniższa tabela zawiera podsumowanie właściwości pierwotnych typów F #.</span><span class="sxs-lookup"><span data-stu-id="53516-107">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="53516-108">Typ</span><span class="sxs-lookup"><span data-stu-id="53516-108">Type</span></span>|<span data-ttu-id="53516-109">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="53516-109">.NET type</span></span>|<span data-ttu-id="53516-110">Opis</span><span class="sxs-lookup"><span data-stu-id="53516-110">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="53516-111">Możliwe wartości to `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="53516-111">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="53516-112">Wartości z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="53516-112">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="53516-113">Wartości od -128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="53516-113">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="53516-114">Wartości od -32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="53516-114">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="53516-115">Wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="53516-115">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="53516-116">Wartości od -2,147,483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="53516-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="53516-117">Wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="53516-117">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="53516-118">Wartości od-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="53516-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="53516-119">Wartości z zakresu od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="53516-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="53516-120">Wskaźnik natywny jako liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="53516-120">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="53516-121">Wskaźnik natywny jako liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="53516-121">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="53516-122">Wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="53516-122">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="53516-123">Tekst Unicode.</span><span class="sxs-lookup"><span data-stu-id="53516-123">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="53516-124">Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.</span><span class="sxs-lookup"><span data-stu-id="53516-124">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="53516-125">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53516-125">not applicable</span></span>|<span data-ttu-id="53516-126">Wskazuje brak rzeczywistą wartość.</span><span class="sxs-lookup"><span data-stu-id="53516-126">Indicates the absence of an actual value.</span></span> <span data-ttu-id="53516-127">Typ ma tylko jeden formalny wartość, która jest oznaczona `()`.</span><span class="sxs-lookup"><span data-stu-id="53516-127">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="53516-128">Wartość jednostki `()`, jest często używana jako symbol zastępczy, gdy wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.</span><span class="sxs-lookup"><span data-stu-id="53516-128">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="53516-129">Wskazuje nie typem lub wartością.</span><span class="sxs-lookup"><span data-stu-id="53516-129">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="53516-130">32-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="53516-130">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="53516-131">64-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="53516-131">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="53516-132">Można wykonać obliczenia z liczb całkowitych za duża dla typu 64-bitową liczbę całkowitą przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="53516-132">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="53516-133">`bigint` nie jest uznawany za typ pierwotny; jest skrótem `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="53516-133">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="53516-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53516-134">See Also</span></span>
[<span data-ttu-id="53516-135">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="53516-135">F# Language Reference</span></span>](index.md)
