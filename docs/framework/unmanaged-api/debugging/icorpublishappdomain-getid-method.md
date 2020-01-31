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
ms.openlocfilehash: 8d6e130981693268ae5c2cd615036b84ca8ed2d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790695"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="919b3-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="919b3-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="919b3-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="919b3-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="919b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="919b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="919b3-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="919b3-106">określoną Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="919b3-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919b3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="919b3-107">Remarks</span></span>  
 <span data-ttu-id="919b3-108">Identyfikator jest unikatowy tylko w zakresie procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="919b3-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919b3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="919b3-109">Requirements</span></span>  
 <span data-ttu-id="919b3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919b3-111">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="919b3-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="919b3-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="919b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="919b3-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919b3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="919b3-114">See also</span></span>

- [<span data-ttu-id="919b3-115">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="919b3-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
