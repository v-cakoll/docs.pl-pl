---
title: IMetaDataEmit2::SaveDeltaToMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 38d0d794cdedfd058b93785f4f444b4dd3196195
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="12117-102">IMetaDataEmit2::SaveDeltaToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="12117-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="12117-103">Zapisuje zmiany z bieżącej sesji edit-and-continue pamięci.</span><span class="sxs-lookup"><span data-stu-id="12117-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12117-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12117-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12117-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12117-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="12117-106">[out] Adres, pod który rozpocząć pisanie zmiana metadanych.</span><span class="sxs-lookup"><span data-stu-id="12117-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="12117-107">[in] Rozmiar zmiany.</span><span class="sxs-lookup"><span data-stu-id="12117-107">[in] The size of the changes.</span></span> <span data-ttu-id="12117-108">Użyj [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) do określenia rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="12117-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12117-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12117-109">Requirements</span></span>  
 <span data-ttu-id="12117-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12117-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12117-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12117-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12117-112">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12117-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12117-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12117-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12117-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12117-114">See Also</span></span>  
 [<span data-ttu-id="12117-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="12117-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="12117-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="12117-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
