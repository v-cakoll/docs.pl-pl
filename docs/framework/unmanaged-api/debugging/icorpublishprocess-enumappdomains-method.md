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
ms.openlocfilehash: 173a7d6793bec9262efb661d56e3a371d0bf9b47
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164609"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="2a5ab-102">ICorPublishProcess::EnumAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="2a5ab-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="2a5ab-103">Pobiera moduł wyliczający dla domen aplikacji w procesie, który odwołuje się do niej to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ab-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a5ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a5ab-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a5ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2a5ab-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2a5ab-106">[out] Wskaźnik na adres [icorpublishappdomainenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) wystąpienia, która umożliwia iteracji przez kolekcję domen aplikacji w ramach tego procesu.</span><span class="sxs-lookup"><span data-stu-id="2a5ab-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a5ab-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a5ab-107">Remarks</span></span>  
 <span data-ttu-id="2a5ab-108">Lista domen aplikacji jest oparte na migawkach domen aplikacji, które istnieją podczas `EnumAppDomains` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2a5ab-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="2a5ab-109">Ta metoda może być wywoływana więcej niż raz utworzyć nową listę aktualne.</span><span class="sxs-lookup"><span data-stu-id="2a5ab-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="2a5ab-110">Kolejne wywołania tej metody nie wpłynie istniejące listy.</span><span class="sxs-lookup"><span data-stu-id="2a5ab-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="2a5ab-111">Jeśli proces został zakończony, `EnumAppDomains` zakończy się niepowodzeniem z wartością HRESULT w CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="2a5ab-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a5ab-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a5ab-112">Requirements</span></span>  
 <span data-ttu-id="2a5ab-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a5ab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a5ab-114">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2a5ab-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2a5ab-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a5ab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a5ab-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a5ab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a5ab-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a5ab-117">See also</span></span>

- [<span data-ttu-id="2a5ab-118">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="2a5ab-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
