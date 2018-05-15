---
title: ICorDebugStackWalk — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 612e0f84302d5bee6479264ef2dbba4c7152657e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="6cd11-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6cd11-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="6cd11-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="6cd11-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cd11-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6cd11-104">Methods</span></span>  
  
|<span data-ttu-id="6cd11-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-105">Method</span></span>|<span data-ttu-id="6cd11-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6cd11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cd11-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="6cd11-108">Zwraca kontekst dla bieżącej ramki `ICorDebugStackWalk` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6cd11-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="6cd11-109">SetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="6cd11-110">Ustawia `ICorDebugStackWalk` bieżący kontekst obiektu do prawidłowego kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="6cd11-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="6cd11-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="6cd11-112">Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="6cd11-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="6cd11-113">GetFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="6cd11-114">Pobiera bieżącą ramkę w `ICorDebugStackWalk` obiektu.</span><span class="sxs-lookup"><span data-stu-id="6cd11-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cd11-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cd11-115">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cd11-116">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="6cd11-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd11-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cd11-117">Requirements</span></span>  
 <span data-ttu-id="6cd11-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd11-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd11-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cd11-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cd11-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cd11-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cd11-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd11-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd11-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cd11-122">See Also</span></span>  
 [<span data-ttu-id="6cd11-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6cd11-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6cd11-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6cd11-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
