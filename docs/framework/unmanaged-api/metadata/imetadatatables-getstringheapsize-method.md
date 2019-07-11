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
ms.openlocfilehash: b842fb4d0853f473ae8e237a42e800cf0af8dc11
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781386"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="7e977-102">IMetaDataTables::GetStringHeapSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="7e977-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="7e977-103">Pobiera rozmiar w bajtach stercie będącej ciągiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="7e977-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e977-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e977-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e977-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e977-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="7e977-106">[out] Wskaźnik do rozmiaru, w bajtach stercie będącej ciągiem tekstowym.</span><span class="sxs-lookup"><span data-stu-id="7e977-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e977-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e977-107">Requirements</span></span>  
 <span data-ttu-id="7e977-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e977-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e977-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7e977-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e977-110">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e977-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7e977-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e977-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e977-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e977-112">See also</span></span>

- [<span data-ttu-id="7e977-113">IMetaDataTables, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e977-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="7e977-114">IMetaDataTables2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e977-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
