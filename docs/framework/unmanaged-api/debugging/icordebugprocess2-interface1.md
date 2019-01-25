---
title: ICorDebugProcess2 Interface1
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
ms.openlocfilehash: 0b37cb8ecd178b90a4dcd2d2eab9fa7c4cd3211d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647325"
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="9240d-102">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="9240d-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="9240d-103">Logiczne rozszerzenie icordebugprocess — interfejs, który reprezentuje proces uruchamiania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9240d-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9240d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9240d-104">Methods</span></span>  
  
|<span data-ttu-id="9240d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-105">Method</span></span>|<span data-ttu-id="9240d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9240d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9240d-107">ClearUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="9240d-108">Usuwa punkt przerwania od określonego przesunięcia, która została ustawiona przez podczas wcześniejszego wywołania `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="9240d-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="9240d-109">GetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="9240d-110">Pobiera flagi, które musi być ustawiona dla środowisko uruchomieniowe języka wspólnego (CLR) w celu załadowania obrazu w procesie przywoływane przez to `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="9240d-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="9240d-111">GetReferenceValueFromGCHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="9240d-112">Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma obsługiwać wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9240d-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="9240d-113">GetThreadForTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="9240d-114">Pobiera wątku, na którym jest wykonywane zadanie o podanym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="9240d-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="9240d-115">GetVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="9240d-116">Pobiera wersję środowiska CLR, w którym jest uruchomiony debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="9240d-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="9240d-117">SetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="9240d-118">Ustawia flagi, które są wymagane przez kompilator just-in-time (JIT) do załadowania obrazu do debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="9240d-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="9240d-119">SetUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="9240d-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="9240d-120">Ustawia niezarządzany punkt przerwania w przesunięciu określonego obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="9240d-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9240d-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9240d-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9240d-122">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="9240d-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9240d-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9240d-123">Requirements</span></span>  
 <span data-ttu-id="9240d-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9240d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9240d-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9240d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9240d-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9240d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9240d-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9240d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9240d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9240d-128">See also</span></span>
- [<span data-ttu-id="9240d-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9240d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
