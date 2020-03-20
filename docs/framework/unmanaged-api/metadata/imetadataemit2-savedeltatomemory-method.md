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
ms.openlocfilehash: 5ec4fe2a8e949cf6e9aa0ce68f4d4e49b72170b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177437"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="b2587-102">IMetaDataEmit2::SaveDeltaToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2587-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="b2587-103">Zapisuje zmiany z bieżącej sesji edycji i kontynuowania w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b2587-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2587-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2587-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2587-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2587-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="b2587-106">[na zewnątrz] Adres, pod którym można rozpocząć pisanie delta metadanych.</span><span class="sxs-lookup"><span data-stu-id="b2587-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="b2587-107">[w] Rozmiar zmian.</span><span class="sxs-lookup"><span data-stu-id="b2587-107">[in] The size of the changes.</span></span> <span data-ttu-id="b2587-108">Użyj [IMetaDataEmit2::GetDeltaSaveSize,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) aby określić rozmiar.</span><span class="sxs-lookup"><span data-stu-id="b2587-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2587-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2587-109">Requirements</span></span>  
 <span data-ttu-id="b2587-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2587-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2587-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2587-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2587-112">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2587-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2587-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2587-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2587-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2587-114">See also</span></span>

- [<span data-ttu-id="b2587-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2587-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="b2587-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2587-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
