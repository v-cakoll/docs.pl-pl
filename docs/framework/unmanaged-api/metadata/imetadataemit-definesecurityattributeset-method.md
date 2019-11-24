---
title: IMetaDataEmit::DefineSecurityAttributeSet — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: b98fab6c6127c3f78151d3b84160d4ca0434b6cd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428249"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="a07ea-102">IMetaDataEmit::DefineSecurityAttributeSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="a07ea-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>
<span data-ttu-id="a07ea-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="a07ea-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a07ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a07ea-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (   
    [in]  mdToken       tkObj,   
    [in]  COR_SECATTR   rSecAttrs[],   
    [in]  ULONG         cSecAttrs,   
    [out] ULONG         *pulErrorAttr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a07ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a07ea-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="a07ea-106">[in] The token to which the security information is attached.</span><span class="sxs-lookup"><span data-stu-id="a07ea-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="a07ea-107">[in] An array of `COR_SECATTR` structures.</span><span class="sxs-lookup"><span data-stu-id="a07ea-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="a07ea-108">[in] The number of elements in `rSecAttrs`.</span><span class="sxs-lookup"><span data-stu-id="a07ea-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="a07ea-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span><span class="sxs-lookup"><span data-stu-id="a07ea-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a07ea-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a07ea-110">Requirements</span></span>  
 <span data-ttu-id="a07ea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a07ea-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a07ea-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a07ea-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a07ea-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a07ea-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a07ea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a07ea-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07ea-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a07ea-115">See also</span></span>

- [<span data-ttu-id="a07ea-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a07ea-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a07ea-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a07ea-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
