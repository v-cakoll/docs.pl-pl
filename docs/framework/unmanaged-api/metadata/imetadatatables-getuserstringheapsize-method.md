---
title: IMetaDataTables::GetUserStringHeapSize — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1215da0816c1fc7cdfaee0da167118909f8e5eb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466105"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="bb55b-102">IMetaDataTables::GetUserStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb55b-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="bb55b-103">Pobiera rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb55b-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb55b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb55b-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb55b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb55b-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="bb55b-106">[out] Wskaźnik do rozmiaru, w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb55b-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb55b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb55b-107">Requirements</span></span>  
 <span data-ttu-id="bb55b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb55b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb55b-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bb55b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb55b-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb55b-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb55b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb55b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb55b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb55b-112">See also</span></span>
- [<span data-ttu-id="bb55b-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb55b-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="bb55b-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb55b-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
