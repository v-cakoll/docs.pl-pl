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
ms.openlocfilehash: 6a7541a2093fe877fb84a8a05237f18c4da43c44
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465988"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="d7af1-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7af1-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="d7af1-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d7af1-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7af1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7af1-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7af1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7af1-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="d7af1-106">[out] Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d7af1-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7af1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7af1-107">Remarks</span></span>  
 <span data-ttu-id="d7af1-108">Identyfikator jest unikatowy tylko w zakresie zawierających procesu.</span><span class="sxs-lookup"><span data-stu-id="d7af1-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7af1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7af1-109">Requirements</span></span>  
 <span data-ttu-id="d7af1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7af1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7af1-111">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d7af1-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d7af1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7af1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7af1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7af1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7af1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7af1-114">See also</span></span>
- [<span data-ttu-id="d7af1-115">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7af1-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
