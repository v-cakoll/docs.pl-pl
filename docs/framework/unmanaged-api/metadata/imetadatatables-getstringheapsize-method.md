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
ms.openlocfilehash: 1aa7853602c1aaf484ef89d9c4fb06464e135f80
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501176"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="cd850-102">IMetaDataTables::GetStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd850-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="cd850-103">Pobiera rozmiar sterty ciągu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="cd850-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd850-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd850-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd850-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd850-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="cd850-106">określoną Wskaźnik do rozmiaru, w bajtach, sterty ciągu.</span><span class="sxs-lookup"><span data-stu-id="cd850-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd850-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd850-107">Requirements</span></span>  
 <span data-ttu-id="cd850-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd850-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd850-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cd850-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd850-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cd850-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd850-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd850-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd850-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd850-112">See also</span></span>

- [<span data-ttu-id="cd850-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd850-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="cd850-114">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cd850-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
