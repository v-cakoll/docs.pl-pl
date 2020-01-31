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
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791880"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="d45e2-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d45e2-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="d45e2-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="d45e2-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d45e2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d45e2-104">Methods</span></span>  
  
|<span data-ttu-id="d45e2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d45e2-105">Method</span></span>|<span data-ttu-id="d45e2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d45e2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d45e2-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="d45e2-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="d45e2-108">Zwraca kontekst dla bieżącej ramki w obiekcie `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="d45e2-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="d45e2-109">SetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="d45e2-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="d45e2-110">Ustawia bieżący kontekst obiektu `ICorDebugStackWalk` na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="d45e2-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="d45e2-111">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="d45e2-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="d45e2-112">Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="d45e2-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="d45e2-113">GetFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="d45e2-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="d45e2-114">Pobiera bieżącą ramkę w obiekcie `ICorDebugStackWalk`.</span><span class="sxs-lookup"><span data-stu-id="d45e2-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d45e2-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d45e2-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d45e2-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d45e2-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d45e2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d45e2-117">Requirements</span></span>  
 <span data-ttu-id="d45e2-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d45e2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d45e2-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d45e2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d45e2-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d45e2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d45e2-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d45e2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d45e2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d45e2-122">See also</span></span>

- [<span data-ttu-id="d45e2-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d45e2-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d45e2-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d45e2-124">Debugging</span></span>](index.md)
