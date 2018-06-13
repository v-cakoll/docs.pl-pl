---
title: IMetaDataTables::GetBlobHeapSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787ea506c6698925473175cf7fdac340c0c2eca8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447281"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="19128-102">IMetaDataTables::GetBlobHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="19128-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="19128-103">Pobiera rozmiar w bajtach sterty dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="19128-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19128-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19128-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="19128-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19128-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="19128-106">[out] Wskaźnik do rozmiar w bajtach sterty obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="19128-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19128-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19128-107">Requirements</span></span>  
 <span data-ttu-id="19128-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19128-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19128-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19128-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19128-110">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19128-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19128-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19128-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19128-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19128-112">See Also</span></span>  
 [<span data-ttu-id="19128-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="19128-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="19128-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19128-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
