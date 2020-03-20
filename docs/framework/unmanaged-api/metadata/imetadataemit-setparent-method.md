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
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175606"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="886e3-102">IMetaDataEmit::SetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="886e3-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="886e3-103">Ustanawia, że określony element członkowski, zgodnie z definicją wcześniejszego wywołania [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), jest członkiem określonego typu, zgodnie z definicją wcześniejszego wywołania [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="886e3-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="886e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="886e3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="886e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="886e3-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="886e3-106">[w] Token, `mdMemberRef` aby otrzymać nowy element nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="886e3-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="886e3-107">[w] Dla `mdToken` nowego rodzica.</span><span class="sxs-lookup"><span data-stu-id="886e3-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="886e3-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="886e3-108">Requirements</span></span>  
 <span data-ttu-id="886e3-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="886e3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="886e3-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="886e3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="886e3-111">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="886e3-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="886e3-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="886e3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886e3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="886e3-113">See also</span></span>

- [<span data-ttu-id="886e3-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="886e3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="886e3-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="886e3-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
