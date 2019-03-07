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
ms.openlocfilehash: 5775c249236fdbe488ce11be0c664d2073ccfb67
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477078"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="f02c6-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="f02c6-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="f02c6-103">Niszczy obiekt odwołuje się określony token metadanych mapowania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="f02c6-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f02c6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f02c6-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f02c6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f02c6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f02c6-106">[in] `mdFieldDef` Lub `mdMethodDef` token, który reprezentuje obiekt, dla której chcesz usunąć metadanych funkcji PInvoke mapowania.</span><span class="sxs-lookup"><span data-stu-id="f02c6-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f02c6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f02c6-107">Requirements</span></span>  
 <span data-ttu-id="f02c6-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f02c6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f02c6-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f02c6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f02c6-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f02c6-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f02c6-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f02c6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f02c6-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f02c6-112">See also</span></span>
- [<span data-ttu-id="f02c6-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f02c6-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f02c6-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f02c6-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
