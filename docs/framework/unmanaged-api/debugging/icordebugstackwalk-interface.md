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
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959675"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="cc76c-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cc76c-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="cc76c-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="cc76c-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc76c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cc76c-104">Methods</span></span>  
  
|<span data-ttu-id="cc76c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cc76c-105">Method</span></span>|<span data-ttu-id="cc76c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cc76c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc76c-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="cc76c-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="cc76c-108">Zwraca kontekst dla bieżącej ramki w `ICorDebugStackWalk` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="cc76c-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="cc76c-109">SetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="cc76c-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="cc76c-110">Ustawia bieżący kontekst obiektu na prawidłowy kontekst dla wątku. `ICorDebugStackWalk`</span><span class="sxs-lookup"><span data-stu-id="cc76c-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="cc76c-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="cc76c-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="cc76c-112">`ICorDebugStackWalk` Przenosi obiekt do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="cc76c-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="cc76c-113">GetFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="cc76c-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="cc76c-114">Pobiera bieżącą ramkę w `ICorDebugStackWalk` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="cc76c-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc76c-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc76c-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc76c-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="cc76c-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc76c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc76c-117">Requirements</span></span>  
 <span data-ttu-id="cc76c-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc76c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc76c-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc76c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc76c-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc76c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc76c-121">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc76c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc76c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc76c-122">See also</span></span>

- [<span data-ttu-id="cc76c-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc76c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cc76c-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cc76c-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
