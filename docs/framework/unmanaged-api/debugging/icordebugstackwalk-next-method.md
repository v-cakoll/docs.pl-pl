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
ms.openlocfilehash: 367c43dc08722288dc3b32b5133f7770ffc3a27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="ace3f-102">ICorDebugStackWalk::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="ace3f-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="ace3f-103">Przenosi [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu do następnej ramki.</span><span class="sxs-lookup"><span data-stu-id="ace3f-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ace3f-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ace3f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ace3f-105">Return Value</span></span>  
 <span data-ttu-id="ace3f-106">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ace3f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ace3f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ace3f-107">HRESULT</span></span>|<span data-ttu-id="ace3f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="ace3f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ace3f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ace3f-109">S_OK</span></span>|<span data-ttu-id="ace3f-110">Środowisko uruchomieniowe pomyślnie odwinięty do następnej ramki (zobacz Uwagi).</span><span class="sxs-lookup"><span data-stu-id="ace3f-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="ace3f-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ace3f-111">E_FAIL</span></span>|<span data-ttu-id="ace3f-112">`ICorDebugStackWalk` Obiektu nie może być zaawansowane.</span><span class="sxs-lookup"><span data-stu-id="ace3f-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="ace3f-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="ace3f-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="ace3f-114">W wyniku tego unwind został osiągnięty koniec stosu.</span><span class="sxs-lookup"><span data-stu-id="ace3f-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="ace3f-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="ace3f-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="ace3f-116">Wskaźnik ramki już znajduje się na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="ace3f-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ace3f-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ace3f-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ace3f-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ace3f-118">Remarks</span></span>  
 <span data-ttu-id="ace3f-119">`Next` Postępu metody `ICorDebugStackWalk` obiektu do wywoływania ramki tylko wtedy, gdy środowisko uruchomieniowe można unwind bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="ace3f-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="ace3f-120">W przeciwnym wypadku obiekt przechodzi do następnej ramki, która może unwind środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ace3f-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace3f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ace3f-121">Requirements</span></span>  
 <span data-ttu-id="ace3f-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ace3f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace3f-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ace3f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ace3f-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ace3f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace3f-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace3f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace3f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ace3f-126">See Also</span></span>  
 [<span data-ttu-id="ace3f-127">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="ace3f-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="ace3f-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ace3f-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ace3f-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ace3f-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
