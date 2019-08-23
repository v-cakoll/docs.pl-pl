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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d66a1aed1936d0146d42c8e4a5ad06dfa39c802
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962963"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="d0e6f-102">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d0e6f-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="d0e6f-103">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="d0e6f-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0e6f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d0e6f-104">Methods</span></span>  
  
|<span data-ttu-id="d0e6f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0e6f-105">Method</span></span>|<span data-ttu-id="d0e6f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d0e6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0e6f-107">GetBlockingObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="d0e6f-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="d0e6f-108">Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="d0e6f-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="d0e6f-109">HadUnhandledException, metoda</span><span class="sxs-lookup"><span data-stu-id="d0e6f-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="d0e6f-110">Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d0e6f-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="d0e6f-111">GetCurrentCustomDebuggerNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="d0e6f-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="d0e6f-112">Pobiera bieżący obiekt [ICorDebugManagedCallback3:: CustomNotification —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="d0e6f-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0e6f-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0e6f-113">Remarks</span></span>  
 <span data-ttu-id="d0e6f-114">Ten interfejs jest logicznym rozszerzeniem interfejsów ICorDebugThread, ICorDebugThread2 i [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d0e6f-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0e6f-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d0e6f-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0e6f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0e6f-116">Requirements</span></span>  
 <span data-ttu-id="d0e6f-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0e6f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0e6f-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0e6f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0e6f-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0e6f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0e6f-120">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0e6f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e6f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0e6f-121">See also</span></span>

- [<span data-ttu-id="d0e6f-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d0e6f-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d0e6f-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d0e6f-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
