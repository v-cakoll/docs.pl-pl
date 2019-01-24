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
ms.openlocfilehash: 8a18e079f84d8adf2cc6f9bd22b35eb1445eaaf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585019"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="20a2a-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="20a2a-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="20a2a-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="20a2a-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20a2a-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20a2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20a2a-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="20a2a-106">[out] Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="20a2a-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20a2a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20a2a-107">Remarks</span></span>  
 <span data-ttu-id="20a2a-108">Identyfikator jest unikatowy tylko w zakresie zawierających procesu.</span><span class="sxs-lookup"><span data-stu-id="20a2a-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a2a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20a2a-109">Requirements</span></span>  
 <span data-ttu-id="20a2a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a2a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a2a-111">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="20a2a-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="20a2a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20a2a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20a2a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20a2a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a2a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20a2a-114">See also</span></span>
- [<span data-ttu-id="20a2a-115">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="20a2a-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
