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
ms.openlocfilehash: 45f40dcd419e8e2fdf8a3349ccc9461854ad9aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175736"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="1edf8-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="1edf8-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="1edf8-103">Niszczy PInvoke mapowania metadanych dla obiektu, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="1edf8-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1edf8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1edf8-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1edf8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1edf8-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1edf8-106">[w] Lub `mdFieldDef` `mdMethodDef` token, który reprezentuje obiekt, dla którego należy usunąć metadane mapowania PInvoke.</span><span class="sxs-lookup"><span data-stu-id="1edf8-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1edf8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1edf8-107">Requirements</span></span>  
 <span data-ttu-id="1edf8-108">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1edf8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1edf8-109">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="1edf8-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1edf8-110">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1edf8-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1edf8-111">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1edf8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edf8-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1edf8-112">See also</span></span>

- [<span data-ttu-id="1edf8-113">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1edf8-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1edf8-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1edf8-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
