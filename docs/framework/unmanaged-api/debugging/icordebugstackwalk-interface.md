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
ms.openlocfilehash: 48f1b485b6dfa8fd898f6ea00eee2d7b397deba6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131858"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="7a3ed-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7a3ed-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="7a3ed-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a3ed-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7a3ed-104">Methods</span></span>  
  
|<span data-ttu-id="7a3ed-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a3ed-105">Method</span></span>|<span data-ttu-id="7a3ed-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7a3ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a3ed-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="7a3ed-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="7a3ed-108">Zwraca kontekst dla bieżącej ramki w obiekcie `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="7a3ed-109">SetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="7a3ed-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="7a3ed-110">Ustawia bieżący kontekst obiektu `ICorDebugStackWalk` na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="7a3ed-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="7a3ed-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="7a3ed-112">Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="7a3ed-113">GetFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="7a3ed-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="7a3ed-114">Pobiera bieżącą ramkę w obiekcie `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a3ed-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a3ed-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a3ed-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="7a3ed-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3ed-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a3ed-117">Requirements</span></span>  
 <span data-ttu-id="7a3ed-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3ed-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3ed-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7a3ed-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a3ed-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7a3ed-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3ed-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3ed-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3ed-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a3ed-122">See also</span></span>

- [<span data-ttu-id="7a3ed-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7a3ed-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7a3ed-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7a3ed-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
