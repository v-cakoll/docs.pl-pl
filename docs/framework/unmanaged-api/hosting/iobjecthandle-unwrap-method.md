---
title: IObjectHandle::Unwrap — Metoda
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5539d77b93be1f56102970e9febe6f63599d78e7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502972"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="2f74b-102">IObjectHandle::Unwrap — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f74b-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="2f74b-103">Dekoduje obiekt marshal przez wartość pośredni.</span><span class="sxs-lookup"><span data-stu-id="2f74b-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f74b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f74b-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f74b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f74b-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="2f74b-106">[out] Wskaźnik do obiektu do odkodowania.</span><span class="sxs-lookup"><span data-stu-id="2f74b-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f74b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f74b-107">Requirements</span></span>  
 <span data-ttu-id="2f74b-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f74b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f74b-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2f74b-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f74b-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f74b-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f74b-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f74b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f74b-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f74b-112">See also</span></span>

