---
title: Typy pierwotne (F#)
description: "Poznaj podstawowe typy pierwotne, które są używane w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f23d98b-551b-4fd2-9f4f-0fd7254288ed
ms.openlocfilehash: b493cdf7116d94f66940d03b86e584bcecbbb0f1
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/08/2017
---
# <a name="primitive-types"></a><span data-ttu-id="9adb7-104">Typy pierwotne</span><span class="sxs-lookup"><span data-stu-id="9adb7-104">Primitive Types</span></span>

<span data-ttu-id="9adb7-105">Ten temat zawiera podstawowe typy pierwotne, które są używane w języku F #.</span><span class="sxs-lookup"><span data-stu-id="9adb7-105">This topic lists the fundamental primitive types that are used in the F# language.</span></span> <span data-ttu-id="9adb7-106">Dla każdego typu danych umożliwia także odpowiednie typy .NET i wartości minimalną i maksymalną.</span><span class="sxs-lookup"><span data-stu-id="9adb7-106">It also provides the corresponding .NET types and the minimum and maximum values for each type.</span></span>

## <a name="summary-of-primitive-types"></a><span data-ttu-id="9adb7-107">Podsumowanie typów pierwotnych</span><span class="sxs-lookup"><span data-stu-id="9adb7-107">Summary of Primitive Types</span></span>
<span data-ttu-id="9adb7-108">Poniższa tabela zawiera podsumowanie właściwości pierwotnych typów F #.</span><span class="sxs-lookup"><span data-stu-id="9adb7-108">The following table summarizes the properties of the primitive F# types.</span></span>

|<span data-ttu-id="9adb7-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9adb7-109">Type</span></span>|<span data-ttu-id="9adb7-110">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="9adb7-110">.NET type</span></span>|<span data-ttu-id="9adb7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9adb7-111">Description</span></span>|
|----|---------|-----------|
|`bool`|`System.Boolean`|<span data-ttu-id="9adb7-112">Możliwe wartości to `true` i `false`.</span><span class="sxs-lookup"><span data-stu-id="9adb7-112">Possible values are `true` and `false`.</span></span>|
|`byte`|`System.Byte`|<span data-ttu-id="9adb7-113">Wartości z zakresu od 0 do 255.</span><span class="sxs-lookup"><span data-stu-id="9adb7-113">Values from 0 to 255.</span></span>|
|`sbyte`|`System.SByte`|<span data-ttu-id="9adb7-114">Wartości od -128 do 127 znaków.</span><span class="sxs-lookup"><span data-stu-id="9adb7-114">Values from -128 to 127.</span></span>|
|`int16`|`System.Int16`|<span data-ttu-id="9adb7-115">Wartości od -32768 do 32767.</span><span class="sxs-lookup"><span data-stu-id="9adb7-115">Values from -32768 to 32767.</span></span>|
|`uint16`|`System.UInt16`|<span data-ttu-id="9adb7-116">Wartości z zakresu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="9adb7-116">Values from 0 to 65535.</span></span>|
|`int`|`System.Int32`|<span data-ttu-id="9adb7-117">Wartości od -2,147,483,648 do 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="9adb7-117">Values from -2,147,483,648 to 2,147,483,647.</span></span>|
|`uint32`|`System.UInt32`|<span data-ttu-id="9adb7-118">Wartości z zakresu od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="9adb7-118">Values from 0 to 4,294,967,295.</span></span>|
|`int64`|`System.Int64`|<span data-ttu-id="9adb7-119">Wartości od-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807.</span><span class="sxs-lookup"><span data-stu-id="9adb7-119">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|
|`uint64`|`System.UInt64`|<span data-ttu-id="9adb7-120">Wartości z zakresu od 0 do 18,446,744,073,709,551,615.</span><span class="sxs-lookup"><span data-stu-id="9adb7-120">Values from 0 to 18,446,744,073,709,551,615.</span></span>|
|`nativeint`|`System.IntPtr`|<span data-ttu-id="9adb7-121">Wskaźnik natywny jako liczbę całkowitą ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="9adb7-121">A native pointer as a signed integer.</span></span>|
|`unativeint`|`System.UIntPtr`|<span data-ttu-id="9adb7-122">Wskaźnik natywny jako liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="9adb7-122">A native pointer as an unsigned integer.</span></span>|
|`char`|`System.Char`|<span data-ttu-id="9adb7-123">Wartości znakowych Unicode.</span><span class="sxs-lookup"><span data-stu-id="9adb7-123">Unicode character values.</span></span>|
|`string`|`System.String`|<span data-ttu-id="9adb7-124">Tekst Unicode.</span><span class="sxs-lookup"><span data-stu-id="9adb7-124">Unicode text.</span></span>|
|`decimal`|`System.Decimal`|<span data-ttu-id="9adb7-125">Zmiennoprzecinkowa typ danych, który ma co najmniej 28 cyfr znaczących.</span><span class="sxs-lookup"><span data-stu-id="9adb7-125">A floating point data type that has at least 28 significant digits.</span></span>|
|`unit`|<span data-ttu-id="9adb7-126">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="9adb7-126">not applicable</span></span>|<span data-ttu-id="9adb7-127">Wskazuje brak rzeczywistą wartość.</span><span class="sxs-lookup"><span data-stu-id="9adb7-127">Indicates the absence of an actual value.</span></span> <span data-ttu-id="9adb7-128">Typ ma tylko jeden formalny wartość, która jest oznaczona `()`.</span><span class="sxs-lookup"><span data-stu-id="9adb7-128">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="9adb7-129">Wartość jednostki `()`, jest często używana jako symbol zastępczy, gdy wartość jest wymagana, ale nie rzeczywistą wartość jest dostępna lub ma sens.</span><span class="sxs-lookup"><span data-stu-id="9adb7-129">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|
|`void`|`System.Void`|<span data-ttu-id="9adb7-130">Wskazuje nie typem lub wartością.</span><span class="sxs-lookup"><span data-stu-id="9adb7-130">Indicates no type or value.</span></span>|
|`float32, single`|`System.Single`|<span data-ttu-id="9adb7-131">32-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="9adb7-131">A 32-bit floating point type.</span></span>|
|`float, double`|`System.Double`|<span data-ttu-id="9adb7-132">64-bitowych zmiennoprzecinkowych punktu typu.</span><span class="sxs-lookup"><span data-stu-id="9adb7-132">A 64-bit floating point type.</span></span>|

>[!NOTE]
<span data-ttu-id="9adb7-133">Można wykonać obliczenia z liczb całkowitych za duża dla typu 64-bitową liczbę całkowitą przy użyciu [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) typu.</span><span class="sxs-lookup"><span data-stu-id="9adb7-133">You can perform computations with integers too big for the 64-bit integer type by using the [bigint](https://msdn.microsoft.com/library/dc8be18d-4042-46c4-b136-2f21a84f6efa) type.</span></span> <span data-ttu-id="9adb7-134">`bigint`nie jest uznawany za typ pierwotny; jest skrótem `System.Numerics.BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="9adb7-134">`bigint` is not considered a primitive type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9adb7-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9adb7-135">See Also</span></span>
[<span data-ttu-id="9adb7-136">Dokumentacja języka F #</span><span class="sxs-lookup"><span data-stu-id="9adb7-136">F# Language Reference</span></span>](index.md)
