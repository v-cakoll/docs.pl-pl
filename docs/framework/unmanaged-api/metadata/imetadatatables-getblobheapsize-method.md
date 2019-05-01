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
ms.openlocfilehash: d22e61d28e0fbf06fa1cfe9e9ac18a534726f01d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042461"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="a6c82-102">IMetaDataTables::GetBlobHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6c82-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="a6c82-103">Pobiera rozmiar w bajtach sterty dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a6c82-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c82-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6c82-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a6c82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6c82-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="a6c82-106">[out] Wskaźnik do rozmiaru, w bajtach stosu obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="a6c82-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6c82-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6c82-107">Requirements</span></span>  
 <span data-ttu-id="a6c82-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6c82-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6c82-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a6c82-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6c82-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6c82-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6c82-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6c82-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c82-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6c82-112">See also</span></span>

- [<span data-ttu-id="a6c82-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6c82-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a6c82-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6c82-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
