---
title: "IMetaDataTables::GetUserStringHeapSize — Metoda"
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
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b1f4f1b8c3cafb28c2b84867dbe5ac3f8424e8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="24b4b-102">IMetaDataTables::GetUserStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="24b4b-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="24b4b-103">Pobiera rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24b4b-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24b4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24b4b-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24b4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24b4b-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="24b4b-106">[out] Wskaźnik do rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24b4b-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24b4b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24b4b-107">Requirements</span></span>  
 <span data-ttu-id="24b4b-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24b4b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24b4b-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="24b4b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24b4b-110">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24b4b-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24b4b-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24b4b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b4b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24b4b-112">See Also</span></span>  
 [<span data-ttu-id="24b4b-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="24b4b-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="24b4b-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="24b4b-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
