---
title: CorElementType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6057bd48ff4fe3f852f82de2bab972d95fef138c
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868569"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="add75-102">CorElementType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="add75-102">CorElementType Enumeration</span></span>

<span data-ttu-id="add75-103">Określa środowisko uruchomieniowe <xref:System.Type>języka wspólnego, modyfikator typu lub informacje o typie w sygnaturze typu metadanych.</span><span class="sxs-lookup"><span data-stu-id="add75-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="add75-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="add75-104">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="add75-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="add75-105">Members</span></span>

|<span data-ttu-id="add75-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="add75-106">Member</span></span>|<span data-ttu-id="add75-107">Opis</span><span class="sxs-lookup"><span data-stu-id="add75-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="add75-108">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="add75-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="add75-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="add75-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="add75-110">Typ wartości logicznej</span><span class="sxs-lookup"><span data-stu-id="add75-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="add75-111">Typ znaku.</span><span class="sxs-lookup"><span data-stu-id="add75-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="add75-112">1-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="add75-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="add75-113">1-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="add75-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="add75-114">Podpisana 2-bajtowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="add75-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="add75-115">2-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="add75-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="add75-116">Podpisana 4-bajtowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="add75-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="add75-117">4-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="add75-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="add75-118">8-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="add75-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="add75-119">8-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="add75-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="add75-120">4-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="add75-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="add75-121">8-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="add75-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="add75-122">Typ System. String.</span><span class="sxs-lookup"><span data-stu-id="add75-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="add75-123">Modyfikator typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="add75-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="add75-124">Modyfikator typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="add75-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="add75-125">Modyfikator typu wartości.</span><span class="sxs-lookup"><span data-stu-id="add75-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="add75-126">Modyfikator typu klasy.</span><span class="sxs-lookup"><span data-stu-id="add75-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="add75-127">Modyfikator typu zmiennej klasy.</span><span class="sxs-lookup"><span data-stu-id="add75-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="add75-128">Modyfikator typu wielowymiarowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="add75-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="add75-129">Modyfikator typu dla typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="add75-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="add75-130">Wpisane odwołanie.</span><span class="sxs-lookup"><span data-stu-id="add75-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="add75-131">Rozmiar natywnej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="add75-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="add75-132">Rozmiar nieoznaczonej natywnej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="add75-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="add75-133">Wskaźnik do funkcji.</span><span class="sxs-lookup"><span data-stu-id="add75-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="add75-134">Typ elementu System. Object.</span><span class="sxs-lookup"><span data-stu-id="add75-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="add75-135">Modyfikator typu tablicy jednowymiarowej o niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="add75-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="add75-136">Modyfikator typu zmiennej metody.</span><span class="sxs-lookup"><span data-stu-id="add75-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="add75-137">Modyfikator wymaganego języka C.</span><span class="sxs-lookup"><span data-stu-id="add75-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="add75-138">Opcjonalny modyfikator języka C.</span><span class="sxs-lookup"><span data-stu-id="add75-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="add75-139">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="add75-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="add75-140">Nieprawidłowy typ.</span><span class="sxs-lookup"><span data-stu-id="add75-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="add75-141">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="add75-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="add75-142">Modyfikator typu, który jest wskaźnikiem na listę zmiennej liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="add75-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="add75-143">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="add75-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="add75-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="add75-144">Remarks</span></span>

<span data-ttu-id="add75-145">Modyfikatory typu stanowią podstawę do reprezentowania bardziej złożonych typów.</span><span class="sxs-lookup"><span data-stu-id="add75-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="add75-146">Wartość `CorElementType` modyfikatora typu jest stosowana do wartości, która bezpośrednio następuje w sygnaturze typu.</span><span class="sxs-lookup"><span data-stu-id="add75-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="add75-147">Wartość, która następuje po `CorElementType` wartości modyfikatora typu, może `CorElementType` być wartością typu prostego, tokenem metadanych lub inną wartością, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="add75-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="add75-148">Wszystkie liczby (*Liczba*, liczba *argumentów*, *token metadanych*, *ranga*, *Liczba*i powiązana) są przechowywane jako skompresowane liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="add75-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="add75-149">Aby uzyskać szczegółowe informacje, zobacz [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) w witrynie sieci Web ECMA.</span><span class="sxs-lookup"><span data-stu-id="add75-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="add75-150">Modyfikator typu</span><span class="sxs-lookup"><span data-stu-id="add75-150">Type modifier</span></span>|<span data-ttu-id="add75-151">Format</span><span class="sxs-lookup"><span data-stu-id="add75-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="add75-152">ELEMENT_TYPE_PTR \<>wartość `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="add75-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="add75-153">ELEMENT_TYPE_BYREF \<>wartość `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="add75-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="add75-154">ELEMENT_TYPE_VALUETYPE \<>tokenumetadanych `mdTypeDef`</span><span class="sxs-lookup"><span data-stu-id="add75-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="add75-155">ELEMENT_TYPE_CLASS \<>tokenumetadanych `mdTypeDef`</span><span class="sxs-lookup"><span data-stu-id="add75-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="add75-156">Numer \<ELEMENT_TYPE_VAR ></span><span class="sxs-lookup"><span data-stu-id="add75-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="add75-157">\<ELEMENT_TYPE_ARRAY wartość >\<rank >\<count1 >\<bound1 >... `CorElementType` \<countN >\<boundN ></span><span class="sxs-lookup"><span data-stu-id="add75-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="add75-158">ELEMENT_TYPE_GENERICINST \<token \<metadanych > \<liczbę argumentów > > arg1... `mdTypeDef` \<argN ></span><span class="sxs-lookup"><span data-stu-id="add75-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="add75-159">ELEMENT_TYPE_FNPTR \<pełną sygnaturę dla funkcji, w tym konwencją wywoływania ></span><span class="sxs-lookup"><span data-stu-id="add75-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="add75-160">ELEMENT_TYPE_SZARRAY \<>wartość `CorElementType`</span><span class="sxs-lookup"><span data-stu-id="add75-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="add75-161">Numer \<ELEMENT_TYPE_MVAR ></span><span class="sxs-lookup"><span data-stu-id="add75-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="add75-162">ELEMENT_TYPE_\<> lub`mdTypeDef`tokenu metadanych `mdTypeRef`</span><span class="sxs-lookup"><span data-stu-id="add75-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="add75-163">E_T_CMOD_OPT \<> lub`mdTypeDef`tokenu metadanych `mdTypeRef`</span><span class="sxs-lookup"><span data-stu-id="add75-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="add75-164">Wymagania</span><span class="sxs-lookup"><span data-stu-id="add75-164">Requirements</span></span>

<span data-ttu-id="add75-165">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="add75-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="add75-166">**Nagłówki** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="add75-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="add75-167">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add75-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="add75-168">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="add75-168">See also</span></span>

- [<span data-ttu-id="add75-169">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="add75-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
