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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b54f5bb47135bcf56c91cd07b916c959e75b9fb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745328"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="76fff-102">IMetaDataEmit2::DefineGenericParam — Metoda</span><span class="sxs-lookup"><span data-stu-id="76fff-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="76fff-103">Tworzy definicję dla parametru typu ogólnego, a następnie pobiera tokenu służącego do tego parametru typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="76fff-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76fff-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="76fff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76fff-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="76fff-106">[in] `mdTypeDef` Lub `mdMethodDef` token, który reprezentuje metodę lub Konstruktor, który chcesz zdefiniować parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="76fff-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="76fff-107">[in] Indeks parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="76fff-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="76fff-108">[in] Wartość [corgenericparamattr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące typ dla parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="76fff-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="76fff-109">[in] Nazwa parametru.</span><span class="sxs-lookup"><span data-stu-id="76fff-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="76fff-110">[in] Ten parametr jest zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="76fff-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="76fff-111">[in] Tablica zakończony zerem ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="76fff-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="76fff-112">Elementy członkowskie tablicy musi być `mdTypeDef`, `mdTypeRef`, lub `mdTypeSpec` token metadanych.</span><span class="sxs-lookup"><span data-stu-id="76fff-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="76fff-113">[out] Token, który reprezentuje parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="76fff-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76fff-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76fff-114">Requirements</span></span>  
 <span data-ttu-id="76fff-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76fff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76fff-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="76fff-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76fff-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="76fff-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76fff-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76fff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fff-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76fff-119">See also</span></span>
- [<span data-ttu-id="76fff-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="76fff-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="76fff-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="76fff-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
