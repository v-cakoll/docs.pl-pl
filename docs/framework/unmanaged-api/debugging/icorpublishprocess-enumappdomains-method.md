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
ms.openlocfilehash: aa76bf511ff1e1710a7ff86ad2ac97665969f2bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140435"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="595b8-102">ICorPublishProcess::EnumAppDomains — Metoda</span><span class="sxs-lookup"><span data-stu-id="595b8-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="595b8-103">Pobiera moduł wyliczający dla domen aplikacji w procesie, do którego odwołuje się ten [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="595b8-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="595b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="595b8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="595b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="595b8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="595b8-106">określoną Wskaźnik do adresu wystąpienia [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) , który umożliwia iterację w kolekcji domen aplikacji w tym procesie.</span><span class="sxs-lookup"><span data-stu-id="595b8-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="595b8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="595b8-107">Remarks</span></span>  
 <span data-ttu-id="595b8-108">Lista domen aplikacji jest oparta na migawce domen aplikacji, które istnieją, gdy wywoływana jest metoda `EnumAppDomains`.</span><span class="sxs-lookup"><span data-stu-id="595b8-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="595b8-109">Ta metoda może być wywoływana więcej niż raz w celu utworzenia nowej listy aktualnych danych.</span><span class="sxs-lookup"><span data-stu-id="595b8-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="595b8-110">Kolejne wywołania tej metody nie będą miały wpływ na istniejące listy.</span><span class="sxs-lookup"><span data-stu-id="595b8-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="595b8-111">Jeśli proces został zakończony, `EnumAppDomains` zakończy się niepowodzeniem z wartością HRESULT równą CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="595b8-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="595b8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="595b8-112">Requirements</span></span>  
 <span data-ttu-id="595b8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="595b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="595b8-114">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="595b8-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="595b8-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="595b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="595b8-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="595b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="595b8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="595b8-117">See also</span></span>

- [<span data-ttu-id="595b8-118">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="595b8-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
