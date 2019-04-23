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
ms.openlocfilehash: d35231e4c36639722635796891056a8902b95940
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097463"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="d3e92-102">IMetaDataTables::GetUserStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3e92-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="d3e92-103">Pobiera rozmiar w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3e92-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e92-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3e92-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3e92-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3e92-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="d3e92-106">[out] Wskaźnik do rozmiaru, w bajtach sterty ciągu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d3e92-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3e92-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3e92-107">Requirements</span></span>  
 <span data-ttu-id="d3e92-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e92-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e92-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d3e92-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3e92-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3e92-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3e92-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e92-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e92-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3e92-112">See also</span></span>

- [<span data-ttu-id="d3e92-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3e92-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d3e92-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3e92-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
