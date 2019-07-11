---
title: ICorDebugStackWalk::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6c96e64b1197b5762c0ad7dbed5458b5d71a3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760892"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="058ff-102">ICorDebugStackWalk::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="058ff-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="058ff-103">Przenosi [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="058ff-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="058ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="058ff-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="058ff-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="058ff-105">Return Value</span></span>  
 <span data-ttu-id="058ff-106">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="058ff-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="058ff-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="058ff-107">HRESULT</span></span>|<span data-ttu-id="058ff-108">Opis</span><span class="sxs-lookup"><span data-stu-id="058ff-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="058ff-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="058ff-109">S_OK</span></span>|<span data-ttu-id="058ff-110">Środowisko uruchomieniowe pomyślnie odwinięty do następnej ramki (zobacz Uwagi).</span><span class="sxs-lookup"><span data-stu-id="058ff-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="058ff-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="058ff-111">E_FAIL</span></span>|<span data-ttu-id="058ff-112">`ICorDebugStackWalk` Nie może kontynuować obiektu.</span><span class="sxs-lookup"><span data-stu-id="058ff-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="058ff-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="058ff-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="058ff-114">Koniec stosu został osiągnięty w wyniku tego unwind.</span><span class="sxs-lookup"><span data-stu-id="058ff-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="058ff-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="058ff-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="058ff-116">Wskaźnik ramki jest już na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="058ff-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="058ff-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="058ff-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="058ff-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="058ff-118">Remarks</span></span>  
 <span data-ttu-id="058ff-119">`Next` Postępu metoda `ICorDebugStackWalk` obiekt wywołujący ramki, tylko wtedy, gdy środowisko uruchomieniowe może unwind bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="058ff-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="058ff-120">W przeciwnym razie obiekt przechodzi do następnej ramki środowiska uruchomieniowego jest w stanie unwind.</span><span class="sxs-lookup"><span data-stu-id="058ff-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="058ff-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="058ff-121">Requirements</span></span>  
 <span data-ttu-id="058ff-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="058ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="058ff-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="058ff-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="058ff-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="058ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="058ff-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="058ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="058ff-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="058ff-126">See also</span></span>

- [<span data-ttu-id="058ff-127">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="058ff-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="058ff-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="058ff-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="058ff-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="058ff-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
