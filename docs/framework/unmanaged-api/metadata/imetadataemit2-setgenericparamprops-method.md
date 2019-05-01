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
ms.openlocfilehash: 4daf24c1712b18d933da702e9e1ef1cbdbfc3639
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043670"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="aeb5b-102">IMetaDataEmit2::SetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="aeb5b-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="aeb5b-103">Ustawia wartości właściwości dla definicji parametru ogólnego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aeb5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aeb5b-104">Syntax</span></span>  
  
```  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aeb5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aeb5b-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="aeb5b-106">[in] Token dla definicji parametru ogólnego, dla którego mają zostać ustawione wartości.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="aeb5b-107">[in] Wartość [corgenericparamattr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) wyliczenie opisujące typ dla parametru ogólnego.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="aeb5b-108">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-108">[in] Optional.</span></span> <span data-ttu-id="aeb5b-109">Nazwa parametru, do których chcesz ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="aeb5b-110">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="aeb5b-111">[in] Opcjonalnie.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-111">[in] Optional.</span></span> <span data-ttu-id="aeb5b-112">Tablica zakończony zerem ograniczenia typu.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="aeb5b-113">Elementy członkowskie tablicy musi być `mdTypeDef`, `mdTypeRef`, lub `mdTypeSpec` token metadanych.</span><span class="sxs-lookup"><span data-stu-id="aeb5b-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb5b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aeb5b-114">Requirements</span></span>  
 <span data-ttu-id="aeb5b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb5b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb5b-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="aeb5b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aeb5b-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aeb5b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb5b-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb5b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb5b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aeb5b-119">See also</span></span>

- [<span data-ttu-id="aeb5b-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="aeb5b-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="aeb5b-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="aeb5b-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
