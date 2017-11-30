---
title: "ICorDebugStackWalk — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="8da06-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8da06-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="8da06-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="8da06-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8da06-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8da06-104">Methods</span></span>  
  
|<span data-ttu-id="8da06-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8da06-105">Method</span></span>|<span data-ttu-id="8da06-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8da06-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8da06-107">GetContext — metoda</span><span class="sxs-lookup"><span data-stu-id="8da06-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="8da06-108">Zwraca kontekst dla bieżącej ramki `ICorDebugStackWalk` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8da06-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="8da06-109">SetContext — metoda</span><span class="sxs-lookup"><span data-stu-id="8da06-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="8da06-110">Ustawia `ICorDebugStackWalk` bieżący kontekst obiektu do prawidłowego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="8da06-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="8da06-111">Next — metoda</span><span class="sxs-lookup"><span data-stu-id="8da06-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="8da06-112">Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="8da06-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="8da06-113">GetFrame — metoda</span><span class="sxs-lookup"><span data-stu-id="8da06-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="8da06-114">Pobiera bieżącą ramkę w `ICorDebugStackWalk` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8da06-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8da06-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8da06-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8da06-116">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="8da06-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8da06-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8da06-117">Requirements</span></span>  
 <span data-ttu-id="8da06-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8da06-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8da06-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8da06-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8da06-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8da06-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8da06-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8da06-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da06-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8da06-122">See Also</span></span>  
 [<span data-ttu-id="8da06-123">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="8da06-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8da06-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8da06-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
