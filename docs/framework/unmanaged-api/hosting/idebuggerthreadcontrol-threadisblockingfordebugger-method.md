---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805254"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="aa82b-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa82b-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="aa82b-103">Powiadamia hosta, że wątek wysyłający to wywołanie zwrotne ma zostać zablokowany w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="aa82b-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa82b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa82b-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="aa82b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa82b-105">Remarks</span></span>  
 <span data-ttu-id="aa82b-106">`ThreadIsBlockingForDebugger`Metoda zostanie zawsze wywołana w wątku środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="aa82b-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="aa82b-107">`ThreadIsBlockingForDebugger`Metoda zapewnia hostowi możliwość wykonywania innej akcji podczas bloków wątków.</span><span class="sxs-lookup"><span data-stu-id="aa82b-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa82b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa82b-108">Requirements</span></span>  
 <span data-ttu-id="aa82b-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa82b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa82b-110">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa82b-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa82b-111">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa82b-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa82b-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa82b-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa82b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa82b-113">See also</span></span>

- [<span data-ttu-id="aa82b-114">IDebuggerThreadControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa82b-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
