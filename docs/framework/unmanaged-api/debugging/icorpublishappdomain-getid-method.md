---
title: ICorPublishAppDomain::GetID — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1a557191c5649f2ed87cf4f4dfdb4167133e597
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774259"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="946fb-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="946fb-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="946fb-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="946fb-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="946fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="946fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="946fb-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="946fb-106">[out] Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="946fb-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="946fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="946fb-107">Remarks</span></span>  
 <span data-ttu-id="946fb-108">Identyfikator jest unikatowy tylko w zakresie zawierających procesu.</span><span class="sxs-lookup"><span data-stu-id="946fb-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946fb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="946fb-109">Requirements</span></span>  
 <span data-ttu-id="946fb-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="946fb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="946fb-111">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="946fb-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="946fb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="946fb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="946fb-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="946fb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="946fb-114">See also</span></span>

- [<span data-ttu-id="946fb-115">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="946fb-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
