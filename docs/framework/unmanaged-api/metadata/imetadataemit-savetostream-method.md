---
title: "IMetaDataEmit::SaveToStream — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SaveToStream
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 97f65fb6cfb7067ed4e6929772f0f114cedcf787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="f8f69-102">IMetaDataEmit::SaveToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="f8f69-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="f8f69-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream`.</span><span class="sxs-lookup"><span data-stu-id="f8f69-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8f69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8f69-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8f69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8f69-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="f8f69-106">[in] Strumień zapisywalny, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="f8f69-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="f8f69-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="f8f69-107">[in] Reserved.</span></span> <span data-ttu-id="f8f69-108">Musi być równy zero.</span><span class="sxs-lookup"><span data-stu-id="f8f69-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8f69-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8f69-109">Requirements</span></span>  
 <span data-ttu-id="f8f69-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f69-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8f69-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f8f69-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8f69-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8f69-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8f69-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f69-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8f69-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8f69-114">See Also</span></span>  
 [<span data-ttu-id="f8f69-115">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="f8f69-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f8f69-116">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f8f69-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
