---
title: IMetaDataEmit2::DefineGenericParam — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 3898b095809e2b84f71aba2036f4d7a294dfdf6a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444654"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="a1193-102">IMetaDataEmit2::DefineGenericParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1193-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="a1193-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1193-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1193-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (   
    [in]  mdToken         tk,   
    [in]  ULONG           ulParamSeq,   
    [in]  DWORD           dwParamFlags,   
    [in]  LPCWSTR         szname,   
    [in]  DWORD           reserved,   
    [in]  mdToken         rtkConstraints[],   
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1193-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1193-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a1193-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="a1193-107">[in] The index of the generic parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="a1193-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="a1193-109">[in] The name of the parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="a1193-110">[in] This parameter is reserved for future extensibility.</span><span class="sxs-lookup"><span data-stu-id="a1193-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="a1193-111">[in] A zero-terminated array of type constraints.</span><span class="sxs-lookup"><span data-stu-id="a1193-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="a1193-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span><span class="sxs-lookup"><span data-stu-id="a1193-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="a1193-113">[out] A token that represents the generic parameter.</span><span class="sxs-lookup"><span data-stu-id="a1193-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1193-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1193-114">Requirements</span></span>  
 <span data-ttu-id="a1193-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1193-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1193-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a1193-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a1193-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1193-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a1193-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1193-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1193-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1193-119">See also</span></span>

- [<span data-ttu-id="a1193-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1193-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="a1193-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1193-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
