---
title: IGCThreadControl::SuspensionStarting — Metoda
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff0c95ea79978c0b58057ec06fea231f5632c941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702655"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="0df44-102">IGCThreadControl::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="0df44-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="0df44-103">Powiadamia hosta, rozpoczyna środowiska uruchomieniowego zawieszeniu wątku wyrzucania elementów bezużytecznych lub innych zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="0df44-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0df44-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0df44-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0df44-105">Remarks</span></span>  
 <span data-ttu-id="0df44-106">Nie zmienić termin egzaminu żadnych wątków podczas `SuspensionStarting` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0df44-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df44-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0df44-107">Requirements</span></span>  
 <span data-ttu-id="0df44-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df44-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df44-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0df44-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0df44-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0df44-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0df44-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df44-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df44-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0df44-112">See also</span></span>
- [<span data-ttu-id="0df44-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="0df44-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
