---
title: IMetaDataEmit2::SaveDeltaToStream — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
ms.openlocfilehash: 7e8376f3a029b0e3ec51a1e7587dd14b3e7530ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177424"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="d3627-102">IMetaDataEmit2::SaveDeltaToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3627-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="d3627-103">Zapisuje zmiany z bieżącej sesji edycji i kontynuowania do określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="d3627-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3627-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3627-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3627-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3627-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="d3627-106">[w] Wskaźnik interfejsu do zapisywalny strumień, do którego można zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="d3627-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d3627-107">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="d3627-107">[in] Reserved.</span></span> <span data-ttu-id="d3627-108">Ta wartość musi wynosić zero.</span><span class="sxs-lookup"><span data-stu-id="d3627-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3627-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3627-109">Requirements</span></span>  
 <span data-ttu-id="d3627-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3627-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3627-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="d3627-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3627-112">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3627-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3627-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3627-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3627-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3627-114">See also</span></span>

- [<span data-ttu-id="d3627-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3627-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="d3627-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d3627-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
