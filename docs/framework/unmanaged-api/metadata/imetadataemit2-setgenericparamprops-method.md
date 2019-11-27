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
ms.openlocfilehash: 7a93bbe0d7a9d9e6ff7505bbc215efa79176ad1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440435"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="bd108-102">IMetaDataEmit2::SetGenericParamProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd108-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="bd108-103">Ustawia wartości właściwości dla definicji parametru generycznego, do której odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="bd108-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd108-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd108-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd108-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd108-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="bd108-106">podczas Token dla definicji parametru generycznego, dla którego mają zostać ustawione wartości.</span><span class="sxs-lookup"><span data-stu-id="bd108-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="bd108-107">podczas Wartość wyliczenia [CorGenericParamAttr —](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) opisująca typ parametru generycznego.</span><span class="sxs-lookup"><span data-stu-id="bd108-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="bd108-108">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="bd108-108">[in] Optional.</span></span> <span data-ttu-id="bd108-109">Nazwa parametru, dla którego mają zostać ustawione wartości.</span><span class="sxs-lookup"><span data-stu-id="bd108-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="bd108-110">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="bd108-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="bd108-111">podczas Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="bd108-111">[in] Optional.</span></span> <span data-ttu-id="bd108-112">Tablica zakończona zerem z ograniczeniami typu.</span><span class="sxs-lookup"><span data-stu-id="bd108-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="bd108-113">Elementy członkowskie tablicy muszą być tokenem metadanych `mdTypeDef`, `mdTypeRef`lub `mdTypeSpec`.</span><span class="sxs-lookup"><span data-stu-id="bd108-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd108-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd108-114">Requirements</span></span>  
 <span data-ttu-id="bd108-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd108-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd108-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bd108-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd108-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd108-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd108-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd108-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd108-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd108-119">See also</span></span>

- [<span data-ttu-id="bd108-120">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd108-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="bd108-121">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="bd108-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
