---
title: ICorDebugProcess2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965686"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="59fa7-102">ICorDebugProcess2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59fa7-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="59fa7-103">Logiczne rozszerzenie icordebugprocess — interfejs, który reprezentuje proces uruchamiania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="59fa7-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59fa7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59fa7-104">Methods</span></span>  
  
|<span data-ttu-id="59fa7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-105">Method</span></span>|<span data-ttu-id="59fa7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59fa7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59fa7-107">ClearUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="59fa7-108">Usuwa punkt przerwania od określonego przesunięcia, która została ustawiona przez podczas wcześniejszego wywołania `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="59fa7-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="59fa7-109">GetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="59fa7-110">Pobiera flagi, które musi być ustawiona dla środowisko uruchomieniowe języka wspólnego (CLR) w celu załadowania obrazu w procesie przywoływane przez to `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="59fa7-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="59fa7-111">GetReferenceValueFromGCHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="59fa7-112">Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma obsługiwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="59fa7-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="59fa7-113">GetThreadForTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="59fa7-114">Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="59fa7-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="59fa7-115">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="59fa7-116">Pobiera wersję środowiska CLR, w którym jest uruchomiony debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="59fa7-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="59fa7-117">SetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="59fa7-118">Ustawia flagi, które są wymagane przez kompilator just-in-time (JIT) do załadowania obrazu do debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="59fa7-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="59fa7-119">SetUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="59fa7-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="59fa7-120">Ustawia niezarządzany punkt przerwania w przesunięciu określonego obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="59fa7-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59fa7-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59fa7-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59fa7-122">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="59fa7-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59fa7-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59fa7-123">Requirements</span></span>  
 <span data-ttu-id="59fa7-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59fa7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59fa7-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59fa7-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59fa7-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59fa7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59fa7-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59fa7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fa7-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59fa7-128">See also</span></span>
- [<span data-ttu-id="59fa7-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="59fa7-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
