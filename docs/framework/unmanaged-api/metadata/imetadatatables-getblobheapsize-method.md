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
ms.openlocfilehash: 68e29e932e477f286db00b0c989a3346bd13c9bc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501225"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="82814-102">IMetaDataTables::GetBlobHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="82814-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="82814-103">Pobiera rozmiar (w bajtach) sterty dużych obiektów binarnych (BLOB).</span><span class="sxs-lookup"><span data-stu-id="82814-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82814-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82814-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="82814-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82814-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="82814-106">określoną Wskaźnik do rozmiaru, w bajtach, sterty obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="82814-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82814-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82814-107">Requirements</span></span>  
 <span data-ttu-id="82814-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82814-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82814-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="82814-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82814-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82814-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82814-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82814-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82814-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82814-112">See also</span></span>

- [<span data-ttu-id="82814-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="82814-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="82814-114">IMetaDataTables2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82814-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
