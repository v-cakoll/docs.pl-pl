---
title: IMetaDataEmit::SaveToStream — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 7db27670b72a5018a03d4614b69486f67bcef155
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175684"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="3ce97-102">IMetaDataEmit::SaveToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ce97-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="3ce97-103">Zapisuje wszystkie metadane w bieżącym `IStream`zakresie do określonego .</span><span class="sxs-lookup"><span data-stu-id="3ce97-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce97-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ce97-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ce97-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ce97-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="3ce97-106">[w] Zapisywalny strumień do zapisania.</span><span class="sxs-lookup"><span data-stu-id="3ce97-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="3ce97-107">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="3ce97-107">[in] Reserved.</span></span> <span data-ttu-id="3ce97-108">Musi być zero.</span><span class="sxs-lookup"><span data-stu-id="3ce97-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce97-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ce97-109">Requirements</span></span>  
 <span data-ttu-id="3ce97-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ce97-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ce97-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="3ce97-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ce97-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3ce97-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ce97-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ce97-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce97-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ce97-114">See also</span></span>

- [<span data-ttu-id="3ce97-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ce97-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3ce97-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ce97-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
