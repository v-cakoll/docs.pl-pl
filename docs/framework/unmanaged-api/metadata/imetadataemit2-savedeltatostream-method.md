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
ms.openlocfilehash: a8f46871dde4c664a502c261fc882f3badf0f362
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492761"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="8d442-102">IMetaDataEmit2::SaveDeltaToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d442-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="8d442-103">Zapisuje zmiany z bieżącej sesji Edit-and-Continue do określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="8d442-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d442-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d442-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d442-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d442-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="8d442-106">podczas Wskaźnik interfejsu do zapisywalnego strumienia, do którego mają zostać zapisane zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d442-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="8d442-107">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="8d442-107">[in] Reserved.</span></span> <span data-ttu-id="8d442-108">Ta wartość musi być równa zero.</span><span class="sxs-lookup"><span data-stu-id="8d442-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d442-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d442-109">Requirements</span></span>  
 <span data-ttu-id="8d442-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d442-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d442-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8d442-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d442-112">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d442-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d442-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d442-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d442-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d442-114">See also</span></span>

- [<span data-ttu-id="8d442-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d442-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="8d442-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8d442-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
