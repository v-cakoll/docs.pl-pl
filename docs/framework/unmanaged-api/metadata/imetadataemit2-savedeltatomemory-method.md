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
ms.openlocfilehash: fa95a737747e9153eb844cddd8e0684585b9108b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049976"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="63242-102">IMetaDataEmit2::SaveDeltaToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="63242-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="63242-103">Zapisuje zmiany z bieżącej sesji edit-and-continue pamięci.</span><span class="sxs-lookup"><span data-stu-id="63242-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63242-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63242-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63242-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63242-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="63242-106">[out] Adres, od którego należy rozpocząć pisanie zmiana metadanych.</span><span class="sxs-lookup"><span data-stu-id="63242-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="63242-107">[in] Rozmiar zmiany.</span><span class="sxs-lookup"><span data-stu-id="63242-107">[in] The size of the changes.</span></span> <span data-ttu-id="63242-108">Użyj [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) Określanie rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="63242-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63242-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63242-109">Requirements</span></span>  
 <span data-ttu-id="63242-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63242-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63242-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="63242-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63242-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63242-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63242-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63242-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63242-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63242-114">See also</span></span>

- [<span data-ttu-id="63242-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="63242-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="63242-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="63242-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
