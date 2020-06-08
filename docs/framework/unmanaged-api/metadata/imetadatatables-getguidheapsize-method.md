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
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490357"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="2acad-102">IMetaDataTables::GetGuidHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="2acad-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="2acad-103">Pobiera rozmiar sterty identyfikatora GUID w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2acad-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2acad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2acad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2acad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2acad-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="2acad-106">określoną Wskaźnik do rozmiaru, w bajtach, sterty identyfikatora GUID.</span><span class="sxs-lookup"><span data-stu-id="2acad-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2acad-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2acad-107">Requirements</span></span>  
 <span data-ttu-id="2acad-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2acad-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2acad-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2acad-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2acad-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2acad-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2acad-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2acad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2acad-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2acad-112">See also</span></span>

- [<span data-ttu-id="2acad-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="2acad-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="2acad-114">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2acad-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
