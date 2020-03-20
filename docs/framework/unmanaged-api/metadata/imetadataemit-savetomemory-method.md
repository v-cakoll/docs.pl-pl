---
title: IMetaDataEmit::SaveToMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177578"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="afc84-102">IMetaDataEmit::SaveToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="afc84-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="afc84-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="afc84-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afc84-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afc84-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afc84-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="afc84-106">[na zewnątrz] Adres, pod którym można rozpocząć pisanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="afc84-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="afc84-107">[w] Rozmiar w bajtach przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="afc84-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc84-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afc84-108">Requirements</span></span>  
 <span data-ttu-id="afc84-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afc84-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afc84-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="afc84-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afc84-111">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="afc84-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afc84-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc84-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc84-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afc84-113">See also</span></span>

- [<span data-ttu-id="afc84-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="afc84-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="afc84-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="afc84-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
