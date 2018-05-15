---
title: IMetaDataEmit2::SetGenericParamProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d74ee7512f640ab906f1119f61e4998b5e882eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="334d2-102">IMetaDataEmit2::SetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="334d2-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="334d2-103">Ustawia wartości właściwości dla definicji parametru ogólnego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="334d2-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="334d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="334d2-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="334d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="334d2-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="334d2-106">[in] Token dla definicji parametrów ogólnych, dla którego mają zostać ustawione wartości.</span><span class="sxs-lookup"><span data-stu-id="334d2-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="334d2-107">[in] Wartość [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące typ dla parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="334d2-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="334d2-108">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="334d2-108">[in] Optional.</span></span> <span data-ttu-id="334d2-109">Nazwa parametru, dla którego mają zostać ustawione wartości.</span><span class="sxs-lookup"><span data-stu-id="334d2-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="334d2-110">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="334d2-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="334d2-111">[in] Opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="334d2-111">[in] Optional.</span></span> <span data-ttu-id="334d2-112">Tablica zakończony zerem ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="334d2-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="334d2-113">Elementy członkowskie tablicy musi być `mdTypeDef`, `mdTypeRef`, lub `mdTypeSpec` token metadanych.</span><span class="sxs-lookup"><span data-stu-id="334d2-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="334d2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="334d2-114">Requirements</span></span>  
 <span data-ttu-id="334d2-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="334d2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="334d2-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="334d2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="334d2-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="334d2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="334d2-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="334d2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334d2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="334d2-119">See Also</span></span>  
 [<span data-ttu-id="334d2-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="334d2-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="334d2-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="334d2-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
