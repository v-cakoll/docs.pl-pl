---
title: ICorPublishProcess::EnumAppDomains — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5492d4e1245c6c0ce5c1eb98d25168c5d69d123b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423705"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="28d63-102">ICorPublishProcess::EnumAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="28d63-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="28d63-103">Pobiera moduł wyliczający dla domeny aplikacji w procesie, który odwołuje się do niego to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="28d63-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28d63-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28d63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28d63-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="28d63-106">[out] Wskaźnik do adresu [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienie, które umożliwia iteracji za pomocą kolekcji domeny aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="28d63-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28d63-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28d63-107">Remarks</span></span>  
 <span data-ttu-id="28d63-108">Listy domen aplikacji jest oparte na migawkach domen aplikacji, które istnieją podczas `EnumAppDomains` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="28d63-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="28d63-109">Ta metoda może wywołać więcej niż raz w celu utworzenia nowej listy aktualne.</span><span class="sxs-lookup"><span data-stu-id="28d63-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="28d63-110">Kolejne wywołania tej metody nie będzie mieć wpływ na istniejące listy.</span><span class="sxs-lookup"><span data-stu-id="28d63-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="28d63-111">Jeśli proces został zakończony, `EnumAppDomains` zakończy się niepowodzeniem z wartością HRESULT z CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="28d63-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d63-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28d63-112">Requirements</span></span>  
 <span data-ttu-id="28d63-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d63-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d63-114">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="28d63-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="28d63-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28d63-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d63-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d63-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28d63-117">See Also</span></span>  
 [<span data-ttu-id="28d63-118">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="28d63-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
