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
ms.openlocfilehash: 43599a7e39ca4cc9d27dab43a948dc2f04e5010a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426674"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="1664a-102">IMetaDataTables::GetStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="1664a-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="1664a-103">Pobiera rozmiar sterty ciągu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="1664a-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1664a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1664a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1664a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1664a-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="1664a-106">określoną Wskaźnik do rozmiaru, w bajtach, sterty ciągu.</span><span class="sxs-lookup"><span data-stu-id="1664a-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1664a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1664a-107">Requirements</span></span>  
 <span data-ttu-id="1664a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1664a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1664a-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1664a-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1664a-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1664a-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1664a-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1664a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1664a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1664a-112">See also</span></span>

- [<span data-ttu-id="1664a-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="1664a-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="1664a-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1664a-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
