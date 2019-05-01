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
ms.openlocfilehash: 5ea100ff86286cb98db5aa9fa6f3c12f5d318a90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043137"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="0a7a0-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a7a0-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="0a7a0-103">Niszczy obiekt odwołuje się określony token metadanych mapowania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a7a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a7a0-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a7a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a7a0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0a7a0-106">[in] `mdFieldDef` Lub `mdMethodDef` token, który reprezentuje obiekt, dla której chcesz usunąć metadanych funkcji PInvoke mapowania.</span><span class="sxs-lookup"><span data-stu-id="0a7a0-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a7a0-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a7a0-107">Requirements</span></span>  
 <span data-ttu-id="0a7a0-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a7a0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a7a0-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0a7a0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a7a0-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a7a0-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a7a0-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a7a0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7a0-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a7a0-112">See also</span></span>

- [<span data-ttu-id="0a7a0-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a7a0-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0a7a0-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a7a0-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
