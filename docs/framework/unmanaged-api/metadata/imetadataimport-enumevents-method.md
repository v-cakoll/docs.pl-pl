---
title: IMetaDataImport::EnumEvents — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 4faf8646b81f92ddf65eff15fdc610d275b37864
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440006"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="02443-102">IMetaDataImport::EnumEvents — Metoda</span><span class="sxs-lookup"><span data-stu-id="02443-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="02443-103">Enumerates event definition tokens for the specified TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="02443-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02443-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02443-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02443-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02443-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="02443-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="02443-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="02443-107">[in] The TypeDef token whose event definitions are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="02443-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="02443-108">[out] The array of returned events.</span><span class="sxs-lookup"><span data-stu-id="02443-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="02443-109">[in] The maximum size of the `rEvents` array.</span><span class="sxs-lookup"><span data-stu-id="02443-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="02443-110">[out] The actual number of events returned in `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="02443-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02443-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="02443-111">Return Value</span></span>  
  
|<span data-ttu-id="02443-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02443-112">HRESULT</span></span>|<span data-ttu-id="02443-113">Opis</span><span class="sxs-lookup"><span data-stu-id="02443-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="02443-114">`EnumEvents` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="02443-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="02443-115">There are no events to enumerate.</span><span class="sxs-lookup"><span data-stu-id="02443-115">There are no events to enumerate.</span></span> <span data-ttu-id="02443-116">In that case, `pcEvents` is zero.</span><span class="sxs-lookup"><span data-stu-id="02443-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02443-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02443-117">Requirements</span></span>  
 <span data-ttu-id="02443-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02443-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02443-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="02443-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02443-120">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02443-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02443-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02443-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02443-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02443-122">See also</span></span>

- [<span data-ttu-id="02443-123">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="02443-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02443-124">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="02443-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
