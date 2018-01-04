---
title: "IMetaDataEmit::Save — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.Save
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a11241894116f57889a15a184290cd95f2f4f54f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="24fb6-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="24fb6-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="24fb6-103">Zapisuje wszystkie metadane w bieżącym zakresie pliku pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="24fb6-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24fb6-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24fb6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24fb6-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="24fb6-106">[in] Nazwa pliku, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="24fb6-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="24fb6-107">Jeśli ta wartość jest równa null, w pamięci kopia zostanie zapisana do ostatniego lokalizacji, która została użyta.</span><span class="sxs-lookup"><span data-stu-id="24fb6-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="24fb6-108">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="24fb6-108">[in] Reserved.</span></span> <span data-ttu-id="24fb6-109">Musi być równy zero.</span><span class="sxs-lookup"><span data-stu-id="24fb6-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24fb6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24fb6-110">Requirements</span></span>  
 <span data-ttu-id="24fb6-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24fb6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24fb6-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24fb6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24fb6-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24fb6-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24fb6-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24fb6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fb6-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24fb6-115">See Also</span></span>  
 [<span data-ttu-id="24fb6-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="24fb6-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="24fb6-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="24fb6-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
