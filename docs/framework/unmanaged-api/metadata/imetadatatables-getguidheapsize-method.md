---
title: IMetaDataTables::GetGuidHeapSize — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ddbd1c034708326d75c59f8ed4764156f617b81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781486"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="1dbcc-102">IMetaDataTables::GetGuidHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="1dbcc-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="1dbcc-103">Pobiera rozmiar w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbcc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dbcc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dbcc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1dbcc-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="1dbcc-106">[out] Wskaźnik do rozmiaru, w bajtach sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="1dbcc-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dbcc-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1dbcc-107">Requirements</span></span>  
 <span data-ttu-id="1dbcc-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dbcc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dbcc-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1dbcc-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dbcc-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dbcc-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1dbcc-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dbcc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbcc-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1dbcc-112">See also</span></span>

- [<span data-ttu-id="1dbcc-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="1dbcc-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1dbcc-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1dbcc-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
