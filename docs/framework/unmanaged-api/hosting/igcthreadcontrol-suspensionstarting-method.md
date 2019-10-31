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
ms.openlocfilehash: 1e1d63ab28276f69e5b3a762520db8f8300d05bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134762"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="187b8-102">IGCThreadControl::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="187b8-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="187b8-103">Powiadamia hosta, że środowisko uruchomieniowe rozpoczyna zawieszenie wątku na wyrzucanie elementów bezużytecznych lub inne zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="187b8-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="187b8-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="187b8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="187b8-105">Remarks</span></span>  
 <span data-ttu-id="187b8-106">Nie należy ponownie planować żadnych wątków w trakcie wywołania zwrotnego `SuspensionStarting`.</span><span class="sxs-lookup"><span data-stu-id="187b8-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="187b8-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="187b8-107">Requirements</span></span>  
 <span data-ttu-id="187b8-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="187b8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187b8-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="187b8-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="187b8-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="187b8-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="187b8-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="187b8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187b8-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="187b8-112">See also</span></span>

- [<span data-ttu-id="187b8-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="187b8-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
