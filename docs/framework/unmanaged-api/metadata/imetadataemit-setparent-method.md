---
title: IMetaDataEmit::SetParent — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6006c8892f650eec9528074d54f030d84ee8f88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750883"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="80599-102">IMetaDataEmit::SetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="80599-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="80599-103">Ustali, że określony element członkowski, zgodnie z definicją przez wcześniejsze wywołanie [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), jest członkiem określonego typu, zgodnie z wcześniejszym wywołaniu [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="80599-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80599-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="80599-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80599-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="80599-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="80599-106">[in] `mdMemberRef` Token, aby otrzymać nowy element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="80599-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="80599-107">[in] `mdToken` Na nowym rekordem nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="80599-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80599-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="80599-108">Requirements</span></span>  
 <span data-ttu-id="80599-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80599-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80599-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="80599-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80599-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="80599-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80599-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80599-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80599-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80599-113">See also</span></span>

- [<span data-ttu-id="80599-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="80599-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="80599-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="80599-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
