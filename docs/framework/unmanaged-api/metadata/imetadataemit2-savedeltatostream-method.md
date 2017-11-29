---
title: "IMetaDataEmit2::SaveDeltaToStream — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2.SaveDeltaToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4bab7bd9035c0746b7f789925e23b74e2caade6a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="e0bb4-102">IMetaDataEmit2::SaveDeltaToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0bb4-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="e0bb4-103">Zapisuje zmiany z bieżącej sesji edit-and-continue określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bb4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0bb4-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0bb4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0bb4-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="e0bb4-106">[in] Wskaźnik interfejsu do zapisu strumienia, z którym chcesz zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="e0bb4-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-107">[in] Reserved.</span></span> <span data-ttu-id="e0bb4-108">Ta wartość musi być równy zero.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bb4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0bb4-109">Requirements</span></span>  
 <span data-ttu-id="e0bb4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0bb4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0bb4-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0bb4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0bb4-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0bb4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0bb4-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0bb4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bb4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0bb4-114">See Also</span></span>  
 [<span data-ttu-id="e0bb4-115">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0bb4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="e0bb4-116">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0bb4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
