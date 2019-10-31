---
title: ICorDebugThread4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 8779dbc95a8bef13d45605295bd68b1d3f16851d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122430"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="cbf80-102">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cbf80-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="cbf80-103">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="cbf80-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbf80-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cbf80-104">Methods</span></span>  
  
|<span data-ttu-id="cbf80-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cbf80-105">Method</span></span>|<span data-ttu-id="cbf80-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cbf80-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbf80-107">GetBlockingObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="cbf80-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="cbf80-108">Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="cbf80-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="cbf80-109">HadUnhandledException, metoda</span><span class="sxs-lookup"><span data-stu-id="cbf80-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="cbf80-110">Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cbf80-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="cbf80-111">GetCurrentCustomDebuggerNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="cbf80-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="cbf80-112">Pobiera bieżący obiekt [ICorDebugManagedCallback3:: CustomNotification —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="cbf80-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbf80-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cbf80-113">Remarks</span></span>  
 <span data-ttu-id="cbf80-114">Ten interfejs jest logicznym rozszerzeniem interfejsów ICorDebugThread, ICorDebugThread2 i [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cbf80-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbf80-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="cbf80-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbf80-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cbf80-116">Requirements</span></span>  
 <span data-ttu-id="cbf80-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbf80-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbf80-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbf80-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbf80-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cbf80-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbf80-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbf80-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf80-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbf80-121">See also</span></span>

- [<span data-ttu-id="cbf80-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cbf80-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cbf80-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cbf80-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
