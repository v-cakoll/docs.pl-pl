---
title: "IMetaDataTables2::GetMetaDataStorage — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStorage
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b86542a55c0b4e778dfd956961f5a14a1c9d6f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="db353-102">IMetaDataTables2::GetMetaDataStorage — Metoda</span><span class="sxs-lookup"><span data-stu-id="db353-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="db353-103">Pobiera rozmiar i zawartość z określonej sekcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="db353-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db353-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db353-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db353-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db353-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="db353-106">[w, out] Wskaźnik do sekcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="db353-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="db353-107">[out] Rozmiar strumienia metadanych.</span><span class="sxs-lookup"><span data-stu-id="db353-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db353-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db353-108">Requirements</span></span>  
 <span data-ttu-id="db353-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db353-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db353-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db353-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db353-111">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db353-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db353-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db353-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db353-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db353-113">See Also</span></span>  
 [<span data-ttu-id="db353-114">IMetaDataTables2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="db353-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="db353-115">IMetaDataTables — interfejs</span><span class="sxs-lookup"><span data-stu-id="db353-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
