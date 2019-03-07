---
title: IMetaDataTables::GetStringHeapSize — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a46f7b277987df7e15eb2d534d1bbacc3250f4e1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466014"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="913cb-102">IMetaDataTables::GetStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="913cb-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="913cb-103">Pobiera rozmiar w bajtach stercie będącej ciągiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="913cb-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="913cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="913cb-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="913cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="913cb-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="913cb-106">[out] Wskaźnik do rozmiaru, w bajtach stercie będącej ciągiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="913cb-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="913cb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="913cb-107">Requirements</span></span>  
 <span data-ttu-id="913cb-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="913cb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="913cb-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="913cb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="913cb-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="913cb-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="913cb-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="913cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="913cb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="913cb-112">See also</span></span>
- [<span data-ttu-id="913cb-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="913cb-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="913cb-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="913cb-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
