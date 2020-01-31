---
title: ICorDebugUnmanagedCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
ms.openlocfilehash: fdd2fee11e9353c3aa3faee2b137597e4ba47801
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791182"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="e9542-102">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e9542-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="e9542-103">Zapewnia powiadomienie o zdarzeniach natywnych, które nie są bezpośrednio związane ze środowiskiem uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e9542-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9542-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e9542-104">Methods</span></span>  
  
|<span data-ttu-id="e9542-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9542-105">Method</span></span>|<span data-ttu-id="e9542-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e9542-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9542-107">DebugEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="e9542-107">DebugEvent Method</span></span>](icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="e9542-108">Powiadamia debuger, że zdarzenie natywne zostało wyzwolone.</span><span class="sxs-lookup"><span data-stu-id="e9542-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9542-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9542-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9542-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e9542-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9542-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9542-111">Requirements</span></span>  
 <span data-ttu-id="e9542-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9542-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9542-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9542-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9542-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e9542-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9542-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9542-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9542-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9542-116">See also</span></span>

- [<span data-ttu-id="e9542-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e9542-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
