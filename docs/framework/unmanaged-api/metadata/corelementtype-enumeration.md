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
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007874"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="61279-102">CorElementType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="61279-102">CorElementType Enumeration</span></span>

<span data-ttu-id="61279-103">Określa środowisko uruchomieniowe języka wspólnego <xref:System.Type> , modyfikator typu lub informacje o typie w sygnaturze typu metadanych.</span><span class="sxs-lookup"><span data-stu-id="61279-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="61279-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61279-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="61279-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="61279-105">Members</span></span>

|<span data-ttu-id="61279-106">Członek</span><span class="sxs-lookup"><span data-stu-id="61279-106">Member</span></span>|<span data-ttu-id="61279-107">Opis</span><span class="sxs-lookup"><span data-stu-id="61279-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="61279-108">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="61279-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="61279-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="61279-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="61279-110">Typ wartości logicznej</span><span class="sxs-lookup"><span data-stu-id="61279-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="61279-111">Typ znaku.</span><span class="sxs-lookup"><span data-stu-id="61279-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="61279-112">1-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="61279-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="61279-113">1-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="61279-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="61279-114">Podpisana 2-bajtowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="61279-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="61279-115">2-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="61279-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="61279-116">Podpisana 4-bajtowa liczba całkowita.</span><span class="sxs-lookup"><span data-stu-id="61279-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="61279-117">4-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="61279-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="61279-118">8-bajtowa liczba całkowita ze znakiem.</span><span class="sxs-lookup"><span data-stu-id="61279-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="61279-119">8-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="61279-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="61279-120">4-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="61279-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="61279-121">8-bajtowy zmiennoprzecinkowy.</span><span class="sxs-lookup"><span data-stu-id="61279-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="61279-122">Typ System. String.</span><span class="sxs-lookup"><span data-stu-id="61279-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="61279-123">Modyfikator typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="61279-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="61279-124">Modyfikator typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="61279-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="61279-125">Modyfikator typu wartości.</span><span class="sxs-lookup"><span data-stu-id="61279-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="61279-126">Modyfikator typu klasy.</span><span class="sxs-lookup"><span data-stu-id="61279-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="61279-127">Modyfikator typu zmiennej klasy.</span><span class="sxs-lookup"><span data-stu-id="61279-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="61279-128">Modyfikator typu wielowymiarowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="61279-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="61279-129">Modyfikator typu dla typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="61279-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="61279-130">Wpisane odwołanie.</span><span class="sxs-lookup"><span data-stu-id="61279-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="61279-131">Rozmiar natywnej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="61279-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="61279-132">Rozmiar nieoznaczonej natywnej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="61279-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="61279-133">Wskaźnik do funkcji.</span><span class="sxs-lookup"><span data-stu-id="61279-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="61279-134">Typ elementu System. Object.</span><span class="sxs-lookup"><span data-stu-id="61279-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="61279-135">Modyfikator typu tablicy jednowymiarowej o niższym poziomie.</span><span class="sxs-lookup"><span data-stu-id="61279-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="61279-136">Modyfikator typu zmiennej metody.</span><span class="sxs-lookup"><span data-stu-id="61279-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="61279-137">Modyfikator wymaganego języka C.</span><span class="sxs-lookup"><span data-stu-id="61279-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="61279-138">Opcjonalny modyfikator języka C.</span><span class="sxs-lookup"><span data-stu-id="61279-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="61279-139">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="61279-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="61279-140">Nieprawidłowy typ.</span><span class="sxs-lookup"><span data-stu-id="61279-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="61279-141">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="61279-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="61279-142">Modyfikator typu, który jest wskaźnikiem na listę zmiennej liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="61279-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="61279-143">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="61279-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="61279-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61279-144">Remarks</span></span>

<span data-ttu-id="61279-145">Modyfikatory typu stanowią podstawę do reprezentowania bardziej złożonych typów.</span><span class="sxs-lookup"><span data-stu-id="61279-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="61279-146">`CorElementType`Wartość modyfikatora typu jest stosowana do wartości, która bezpośrednio następuje w sygnaturze typu.</span><span class="sxs-lookup"><span data-stu-id="61279-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="61279-147">Wartość, która następuje po `CorElementType` wartości modyfikatora typu, może być `CorElementType` wartością typu prostego, tokenem metadanych lub inną wartością, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="61279-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="61279-148">Wszystkie liczby (*Liczba*, liczba *argumentów*, *token metadanych*, *ranga*, *Liczba*i *powiązana*) są przechowywane jako skompresowane liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="61279-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="61279-149">Aby uzyskać szczegółowe informacje, zobacz [Standard ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) w witrynie sieci Web ECMA.</span><span class="sxs-lookup"><span data-stu-id="61279-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="61279-150">Modyfikator typu</span><span class="sxs-lookup"><span data-stu-id="61279-150">Type modifier</span></span>|<span data-ttu-id="61279-151">Format</span><span class="sxs-lookup"><span data-stu-id="61279-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="61279-152">ELEMENT_TYPE_PTR\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="61279-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="61279-153">ELEMENT_TYPE_BYREF\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="61279-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="61279-154">ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="61279-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="61279-155">ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="61279-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="61279-156">ELEMENT_TYPE_VAR\<number></span><span class="sxs-lookup"><span data-stu-id="61279-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="61279-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="61279-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="61279-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ...\<argN></span><span class="sxs-lookup"><span data-stu-id="61279-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="61279-159">ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="61279-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="61279-160">ELEMENT_TYPE_SZARRAY\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="61279-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="61279-161">ELEMENT_TYPE_MVAR\<number></span><span class="sxs-lookup"><span data-stu-id="61279-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="61279-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="61279-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="61279-163">E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="61279-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="61279-164">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61279-164">Requirements</span></span>

<span data-ttu-id="61279-165">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61279-165">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="61279-166">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="61279-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="61279-167">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61279-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="61279-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61279-168">See also</span></span>

- [<span data-ttu-id="61279-169">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="61279-169">Metadata Enumerations</span></span>](metadata-enumerations.md)
