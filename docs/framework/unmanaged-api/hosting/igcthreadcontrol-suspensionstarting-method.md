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
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805100"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="d2632-102">IGCThreadControl::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2632-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="d2632-103">Powiadamia hosta, że środowisko uruchomieniowe rozpoczyna zawieszenie wątku na wyrzucanie elementów bezużytecznych lub inne zawieszenie.</span><span class="sxs-lookup"><span data-stu-id="d2632-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2632-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2632-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="d2632-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d2632-105">Remarks</span></span>  
 <span data-ttu-id="d2632-106">Nie należy ponownie planować żadnych wątków w trakcie `SuspensionStarting` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d2632-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2632-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2632-107">Requirements</span></span>  
 <span data-ttu-id="d2632-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2632-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2632-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d2632-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2632-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d2632-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2632-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2632-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2632-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2632-112">See also</span></span>

- [<span data-ttu-id="d2632-113">IGCThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="d2632-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
