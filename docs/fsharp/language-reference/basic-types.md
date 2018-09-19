---
title: 'Typy podstawowe (F #)'
description: 'Poznaj podstawowe typy podstawowe, które są używane w języku F #.'
ms.date: 07/09/2018
ms.openlocfilehash: 8f948d066323527b09b1d3f9f4167b95b1c875cf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45991015"
---
# <a name="basic-types"></a><span data-ttu-id="c08b7-103">Typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="c08b7-103">Basic types</span></span>

<span data-ttu-id="c08b7-104">Ten temat zawiera podstawowe typy, które są zdefiniowane w języku F #.</span><span class="sxs-lookup"><span data-stu-id="c08b7-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="c08b7-105">Te typy są zasadnicze znaczenie w języku F #, na podstawie prawie każdy program F #.</span><span class="sxs-lookup"><span data-stu-id="c08b7-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="c08b7-106">Są one podzbiorem .NET typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="c08b7-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="c08b7-107">Typ</span><span class="sxs-lookup"><span data-stu-id="c08b7-107">Type</span></span>|<span data-ttu-id="c08b7-108">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="c08b7-108">.NET type</span></span>|<span data-ttu-id="c08b7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="c08b7-109">Description</span></span>|
|----|---------|-----------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="c08b7-110">Możliwe wartości to `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="c08b7-110">Possible values are `true` and `false`.</span></span>|
|`byte`|<xref:System.Byte>|<span data-ttu-id="c08b7-111">Wartości z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="c08b7-111">Values from 0 to 255.</span></span>|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="c08b7-112">Wartości od -128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="c08b7-112">Values from -128 to 127.</span></span>|
|`int16`|<xref:System.Int16>|<span data-ttu-id="c08b7-113">Wartości od -32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="c08b7-113">Values from -32768 to 32767.</span></span>|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="c08b7-114">Wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="c08b7-114">Values from 0 to 65535.</span></span>|
|`int`|<xref:System.Int32>|<span data-ttu-id="c08b7-115">Wartości od -2,147,483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="c08b7-115">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|<xref:System.UInt32>|<span data-ttu-id="c08b7-116">Wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="c08b7-116">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|<xref:System.Int64>|<span data-ttu-id="c08b7-117">Wartości z-9,223,372,036,854,775,808 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="c08b7-117">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="c08b7-118">Wartości z zakresu od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="c08b7-118">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="c08b7-119">Wskaźnik natywny jako liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="c08b7-119">A native pointer as a signed integer.</span></span>|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="c08b7-120">Wskaźnik natywny jako liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="c08b7-120">A native pointer as an unsigned integer.</span></span>|
|`char`|<xref:System.Char>|<span data-ttu-id="c08b7-121">Wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="c08b7-121">Unicode character values.</span></span>|
|`string`|<xref:System.String>|<span data-ttu-id="c08b7-122">Tekst w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="c08b7-122">Unicode text.</span></span>|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="c08b7-123">Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.</span><span class="sxs-lookup"><span data-stu-id="c08b7-123">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="c08b7-124">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c08b7-124">not applicable</span></span>|<span data-ttu-id="c08b7-125">Wskazuje brak rzeczywistej wartości.</span><span class="sxs-lookup"><span data-stu-id="c08b7-125">Indicates the absence of an actual value.</span></span> <span data-ttu-id="c08b7-126">Typ ma tylko jedną wartość formalny, która jest oznaczona `()`.</span><span class="sxs-lookup"><span data-stu-id="c08b7-126">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="c08b7-127">Wartość jednostki `()`, jest często używana jako symbol zastępczy, której wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.</span><span class="sxs-lookup"><span data-stu-id="c08b7-127">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|<xref:System.Void>|<span data-ttu-id="c08b7-128">Wskazuje nie typu lub wartości.</span><span class="sxs-lookup"><span data-stu-id="c08b7-128">Indicates no type or value.</span></span>|
|<span data-ttu-id="c08b7-129">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="c08b7-129">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="c08b7-130">32-bitowych punktu typ zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="c08b7-130">A 32-bit floating point type.</span></span>|
|<span data-ttu-id="c08b7-131">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="c08b7-131">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="c08b7-132">64-bitowych punktu typ zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="c08b7-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="c08b7-133">Można wykonać obliczeń na liczbach całkowitych zbyt duży dla typu 64-bitową liczbę całkowitą, przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="c08b7-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="c08b7-134">`bigint` nie jest uważany za typu podstawowego; jest skrótem `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="c08b7-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c08b7-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c08b7-135">See also</span></span>

- [<span data-ttu-id="c08b7-136">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="c08b7-136">F# Language Reference</span></span>](index.md)
