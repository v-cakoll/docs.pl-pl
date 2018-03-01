---
title: "IMetaDataTables::GetGuidHeapSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 297b8f3572f67aa5e8b17b1b94d71f59962cfe68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="f0924-102">IMetaDataTables::GetGuidHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0924-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="f0924-103">Pobiera rozmiar w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="f0924-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0924-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0924-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0924-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0924-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="f0924-106">[out] Wskaźnik do rozmiar w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="f0924-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0924-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0924-107">Requirements</span></span>  
 <span data-ttu-id="f0924-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0924-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0924-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0924-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0924-110">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0924-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0924-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0924-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0924-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0924-112">See Also</span></span>  
 [<span data-ttu-id="f0924-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0924-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="f0924-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0924-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
