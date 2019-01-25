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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0702a7a58e6bd8c13254da5adce17c9adf6fa0cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569465"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="64e88-102">IMetaDataEmit2::SaveDeltaToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="64e88-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="64e88-103">Zapisuje zmiany z bieżącej sesji Edytuj i Kontynuuj do określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="64e88-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64e88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64e88-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64e88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64e88-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="64e88-106">[in] Wskaźnik interfejsu do zapisywalnego strumień, do której chcesz zapisać zmiany.</span><span class="sxs-lookup"><span data-stu-id="64e88-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="64e88-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="64e88-107">[in] Reserved.</span></span> <span data-ttu-id="64e88-108">Ta wartość musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="64e88-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64e88-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64e88-109">Requirements</span></span>  
 <span data-ttu-id="64e88-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64e88-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64e88-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="64e88-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64e88-112">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64e88-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64e88-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64e88-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e88-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64e88-114">See also</span></span>
- [<span data-ttu-id="64e88-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="64e88-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="64e88-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="64e88-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
