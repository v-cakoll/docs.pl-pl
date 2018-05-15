---
title: IMetaDataEmit::DeletePinvokeMap — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34db47b9f43412c9b6c5f58dd6afded505703905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="14f8f-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="14f8f-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="14f8f-103">Niszczy metadanych mapowania PInvoke dla obiekt odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="14f8f-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14f8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14f8f-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14f8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14f8f-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="14f8f-106">[in] `mdFieldDef` Lub `mdMethodDef` token, który reprezentuje obiekt, dla której chcesz usunąć mapowanie metadanych funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="14f8f-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14f8f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14f8f-107">Requirements</span></span>  
 <span data-ttu-id="14f8f-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f8f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14f8f-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14f8f-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14f8f-110">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14f8f-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14f8f-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14f8f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14f8f-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14f8f-112">See Also</span></span>  
 [<span data-ttu-id="14f8f-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="14f8f-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="14f8f-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="14f8f-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
