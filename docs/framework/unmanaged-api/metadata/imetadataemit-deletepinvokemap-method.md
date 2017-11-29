---
title: "IMetaDataEmit::DeletePinvokeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeletePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4ef79c7696f9d697d3306634635c5c00bfd1f00c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="a7ca2-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7ca2-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="a7ca2-103">Niszczy metadanych mapowania PInvoke dla obiekt odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="a7ca2-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ca2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7ca2-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7ca2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7ca2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a7ca2-106">[in] `mdFieldDef` Lub `mdMethodDef` token, który reprezentuje obiekt, dla której chcesz usunąć mapowanie metadanych funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="a7ca2-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ca2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7ca2-107">Requirements</span></span>  
 <span data-ttu-id="a7ca2-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ca2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ca2-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7ca2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7ca2-110">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7ca2-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7ca2-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ca2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ca2-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7ca2-112">See Also</span></span>  
 [<span data-ttu-id="a7ca2-113">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ca2-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a7ca2-114">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7ca2-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
