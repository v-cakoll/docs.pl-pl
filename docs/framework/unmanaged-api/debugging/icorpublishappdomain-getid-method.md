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
ms.openlocfilehash: 33a72d9aea09f808d42d1a17a7ec5640d20d7c79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140373"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="7a3af-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a3af-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="7a3af-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7a3af-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a3af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a3af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a3af-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="7a3af-106">określoną Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7a3af-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a3af-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a3af-107">Remarks</span></span>  
 <span data-ttu-id="7a3af-108">Identyfikator jest unikatowy tylko w zakresie procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="7a3af-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3af-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a3af-109">Requirements</span></span>  
 <span data-ttu-id="7a3af-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3af-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3af-111">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="7a3af-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7a3af-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7a3af-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3af-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3af-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a3af-114">See also</span></span>

- [<span data-ttu-id="7a3af-115">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a3af-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
