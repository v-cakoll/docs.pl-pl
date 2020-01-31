---
title: ICorDebugManagedCallback3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793270"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="31659-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="31659-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="31659-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="31659-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31659-104">Metody</span><span class="sxs-lookup"><span data-stu-id="31659-104">Methods</span></span>  
  
|<span data-ttu-id="31659-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="31659-105">Method</span></span>|<span data-ttu-id="31659-106">Opis</span><span class="sxs-lookup"><span data-stu-id="31659-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31659-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="31659-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="31659-108">Wskazuje, że zostało zgłoszone włączone powiadomienie debugera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="31659-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31659-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31659-109">Remarks</span></span>  
 <span data-ttu-id="31659-110">Ten interfejs jest logicznym rozszerzeniem interfejsów [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="31659-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31659-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="31659-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31659-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31659-112">Requirements</span></span>  
 <span data-ttu-id="31659-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31659-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31659-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31659-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31659-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31659-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31659-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31659-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31659-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31659-117">See also</span></span>

- [<span data-ttu-id="31659-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="31659-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="31659-119">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="31659-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="31659-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="31659-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="31659-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31659-121">Debugging</span></span>](index.md)
