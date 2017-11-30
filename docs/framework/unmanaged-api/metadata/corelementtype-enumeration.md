---
title: CorElementType Enumeration1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorElementType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorElementType
helpviewer_keywords: CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8932e295aa1a6c6cf961e7b3a218e76984da02cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="d601a-102">CorElementType Enumeration1</span><span class="sxs-lookup"><span data-stu-id="d601a-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="d601a-103">Określa środowisko uruchomieniowe języka wspólnego <xref:System.Type>, typ i/lub informacje o typie w podpisie typu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d601a-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d601a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d601a-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d601a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d601a-105">Members</span></span>  
  
|<span data-ttu-id="d601a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d601a-106">Member</span></span>|<span data-ttu-id="d601a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d601a-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="d601a-108">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d601a-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="d601a-109">Typ void.</span><span class="sxs-lookup"><span data-stu-id="d601a-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="d601a-110">Typ Boolean</span><span class="sxs-lookup"><span data-stu-id="d601a-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="d601a-111">Typ znaków.</span><span class="sxs-lookup"><span data-stu-id="d601a-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="d601a-112">Całkowita 1-bajtowego.</span><span class="sxs-lookup"><span data-stu-id="d601a-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="d601a-113">Niepodpisane 1-bajtowych liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d601a-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="d601a-114">Całkowita 2-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="d601a-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="d601a-115">2-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d601a-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="d601a-116">Całkowita 4-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="d601a-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="d601a-117">4-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d601a-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="d601a-118">Całkowita 8-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="d601a-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="d601a-119">8-bajtowa liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="d601a-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="d601a-120">4-bajtowych zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="d601a-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="d601a-121">8-bajtowych zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="d601a-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="d601a-122">Typem System.String.</span><span class="sxs-lookup"><span data-stu-id="d601a-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="d601a-123">Modyfikator typu wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d601a-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="d601a-124">Modyfikator typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="d601a-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="d601a-125">Modyfikator typu wartości.</span><span class="sxs-lookup"><span data-stu-id="d601a-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="d601a-126">Modyfikator typu klasy.</span><span class="sxs-lookup"><span data-stu-id="d601a-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="d601a-127">Modyfikator zmiennej typu klasy.</span><span class="sxs-lookup"><span data-stu-id="d601a-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="d601a-128">Modyfikator typu tablicy wielowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="d601a-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="d601a-129">Modyfikator typu typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d601a-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="d601a-130">Odniesienie typu.</span><span class="sxs-lookup"><span data-stu-id="d601a-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="d601a-131">Rozmiar całkowitą natywnego.</span><span class="sxs-lookup"><span data-stu-id="d601a-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="d601a-132">Rozmiar całkowitą bez znaku macierzystego.</span><span class="sxs-lookup"><span data-stu-id="d601a-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="d601a-133">Wskaźnik do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d601a-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="d601a-134">Typ elementu System.Object.</span><span class="sxs-lookup"><span data-stu-id="d601a-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="d601a-135">Jednowymiarowe, zero modyfikator typu dolna granica tablicy.</span><span class="sxs-lookup"><span data-stu-id="d601a-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="d601a-136">Modyfikator zmiennej typu metody.</span><span class="sxs-lookup"><span data-stu-id="d601a-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="d601a-137">Modyfikator wymagane języka C.</span><span class="sxs-lookup"><span data-stu-id="d601a-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="d601a-138">Modyfikator opcjonalne języka C.</span><span class="sxs-lookup"><span data-stu-id="d601a-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="d601a-139">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d601a-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="d601a-140">Nieprawidłowy typ.</span><span class="sxs-lookup"><span data-stu-id="d601a-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="d601a-141">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d601a-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="d601a-142">Modyfikator typu będącego wartownik listę zmiennych liczba parametrów.</span><span class="sxs-lookup"><span data-stu-id="d601a-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="d601a-143">Używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d601a-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d601a-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d601a-144">Remarks</span></span>  
 <span data-ttu-id="d601a-145">Modyfikatory typu stanowią podstawę reprezentujący bardziej złożonych typów.</span><span class="sxs-lookup"><span data-stu-id="d601a-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="d601a-146">A `CorElementType` typu modyfikator wartość jest stosowana do poniższą w podpisie typu wartości.</span><span class="sxs-lookup"><span data-stu-id="d601a-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="d601a-147">Wartość, która wykonuje `CorElementType` wartość modyfikator typu może być `CorElementType` wartość typu prostego, token metadanych lub inna wartość określoną w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d601a-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d601a-148">Wszystkie numery (*numer*, *argument Count*, *token metadanych*, *rangę*, *liczby*i *powiązany*) są przechowywane w postaci skompresowanej liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d601a-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="d601a-149">Zobacz [standardowe ECMA-335 - infrastruktury języka wspólnego (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) w witrynie sieci Web ECMA, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="d601a-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="d601a-150">Modyfikator typu</span><span class="sxs-lookup"><span data-stu-id="d601a-150">Type modifier</span></span>|<span data-ttu-id="d601a-151">Format</span><span class="sxs-lookup"><span data-stu-id="d601a-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="d601a-152">Poprawności elementu ELEMENT_TYPE_PTR < `CorElementType` wartość ></span><span class="sxs-lookup"><span data-stu-id="d601a-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="d601a-153">ELEMENT_TYPE_BYREF < `CorElementType` wartość ></span><span class="sxs-lookup"><span data-stu-id="d601a-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="d601a-154">ELEMENT_TYPE_VALUETYPE < `mdTypeDef` token metadanych ></span><span class="sxs-lookup"><span data-stu-id="d601a-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="d601a-155">Po elemencie ELEMENT_TYPE_CLASS < `mdTypeDef` token metadanych ></span><span class="sxs-lookup"><span data-stu-id="d601a-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="d601a-156">ELEMENT_TYPE_VAR \<numer ></span><span class="sxs-lookup"><span data-stu-id="d601a-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="d601a-157">ELEMENT_TYPE_ARRAY < `CorElementType` wartość > \<rangę > \<count1 > \<bound1 >... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="d601a-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="d601a-158">ELEMENT_TYPE_GENERICINST < `mdTypeDef` token metadanych > \<argument Count > \<arg1 >... \<argN ></span><span class="sxs-lookup"><span data-stu-id="d601a-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="d601a-159">ELEMENT_TYPE_FNPTR \<pełną podpisu funkcji, łącznie z konwencji wywoływania ></span><span class="sxs-lookup"><span data-stu-id="d601a-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="d601a-160">ELEMENT_TYPE_SZARRAY < `CorElementType` wartość ></span><span class="sxs-lookup"><span data-stu-id="d601a-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="d601a-161">ELEMENT_TYPE_MVAR \<numer ></span><span class="sxs-lookup"><span data-stu-id="d601a-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="d601a-162">Element ELEMENT_TYPE_ < `mdTypeRef` lub `mdTypeDef` token metadanych ></span><span class="sxs-lookup"><span data-stu-id="d601a-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="d601a-163">E_T_CMOD_OPT < `mdTypeRef` lub `mdTypeDef` token metadanych ></span><span class="sxs-lookup"><span data-stu-id="d601a-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d601a-164">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d601a-164">Requirements</span></span>  
 <span data-ttu-id="d601a-165">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d601a-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d601a-166">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d601a-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d601a-167">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d601a-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d601a-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d601a-168">See Also</span></span>  
 [<span data-ttu-id="d601a-169">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d601a-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
