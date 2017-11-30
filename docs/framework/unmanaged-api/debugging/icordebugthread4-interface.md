---
title: "ICorDebugThread4 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4
helpviewer_keywords: ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e54611a38193a05a33381e798a61977d7aec41a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="4b020-102">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4b020-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="4b020-103">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="4b020-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b020-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4b020-104">Methods</span></span>  
  
|<span data-ttu-id="4b020-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4b020-105">Method</span></span>|<span data-ttu-id="4b020-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4b020-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b020-107">GetBlockingObjects — metoda</span><span class="sxs-lookup"><span data-stu-id="4b020-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="4b020-108">Udostępnia w kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="4b020-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="4b020-109">HadUnhandledException — metoda</span><span class="sxs-lookup"><span data-stu-id="4b020-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="4b020-110">Wskazuje, czy wątek nigdy miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4b020-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="4b020-111">GetCurrentCustomDebuggerNotification — metoda</span><span class="sxs-lookup"><span data-stu-id="4b020-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="4b020-112">Pobiera bieżący [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) obiektu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="4b020-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b020-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b020-113">Remarks</span></span>  
 <span data-ttu-id="4b020-114">Ten interfejs jest logiczną rozszerzenia ICorDebugThread, ICorDebugThread2, i [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="4b020-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b020-115">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="4b020-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b020-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b020-116">Requirements</span></span>  
 <span data-ttu-id="4b020-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b020-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b020-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b020-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b020-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b020-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b020-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b020-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b020-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b020-121">See Also</span></span>  
 [<span data-ttu-id="4b020-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4b020-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4b020-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4b020-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
