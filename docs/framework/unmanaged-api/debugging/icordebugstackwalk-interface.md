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
ms.openlocfilehash: 5f71dfcdffaaa683ca4f2abebaa99115ef90e0ff
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378904"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="76050-102">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="76050-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="76050-103">Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.</span><span class="sxs-lookup"><span data-stu-id="76050-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76050-104">Metody</span><span class="sxs-lookup"><span data-stu-id="76050-104">Methods</span></span>  
  
|<span data-ttu-id="76050-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="76050-105">Method</span></span>|<span data-ttu-id="76050-106">Opis</span><span class="sxs-lookup"><span data-stu-id="76050-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76050-107">GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="76050-107">GetContext Method</span></span>](icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="76050-108">Zwraca kontekst dla bieżącej ramki w `ICorDebugStackWalk` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="76050-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="76050-109">SetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="76050-109">SetContext Method</span></span>](icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="76050-110">Ustawia `ICorDebugStackWalk` bieżący kontekst obiektu na prawidłowy kontekst dla wątku.</span><span class="sxs-lookup"><span data-stu-id="76050-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="76050-111">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="76050-111">Next Method</span></span>](icordebugstackwalk-next-method.md)|<span data-ttu-id="76050-112">Przenosi `ICorDebugStackWalk` obiekt do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="76050-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="76050-113">GetFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="76050-113">GetFrame Method</span></span>](icordebugstackwalk-getframe-method.md)|<span data-ttu-id="76050-114">Pobiera bieżącą ramkę w `ICorDebugStackWalk` obiekcie.</span><span class="sxs-lookup"><span data-stu-id="76050-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76050-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76050-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76050-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="76050-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76050-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76050-117">Requirements</span></span>  
 <span data-ttu-id="76050-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76050-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76050-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76050-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76050-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="76050-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76050-121">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76050-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76050-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76050-122">See also</span></span>

- [<span data-ttu-id="76050-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="76050-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="76050-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="76050-124">Debugging</span></span>](index.md)
