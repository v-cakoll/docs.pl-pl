---
title: ICorDebugProcess2, interfejs
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
ms.openlocfilehash: 1a57b7ceb6da961fba1f0d6e8e0ba1aa88ca0541
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213494"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="99bda-102">ICorDebugProcess2, interfejs</span><span class="sxs-lookup"><span data-stu-id="99bda-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="99bda-103">Logiczne rozszerzenie interfejsu ICorDebugProcess, które reprezentuje proces z uruchomionym kodem zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="99bda-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99bda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="99bda-104">Methods</span></span>  
  
|<span data-ttu-id="99bda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-105">Method</span></span>|<span data-ttu-id="99bda-106">Opis</span><span class="sxs-lookup"><span data-stu-id="99bda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99bda-107">ClearUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="99bda-108">Usuwa punkt przerwania w określonym przesunięciu, który został ustawiony przez wcześniejsze wywołanie do `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="99bda-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="99bda-109">GetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="99bda-110">Pobiera flagi, które muszą zostać ustawione dla środowiska uruchomieniowego języka wspólnego (CLR) w celu załadowania obrazu do procesu, do którego się odwołuje `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="99bda-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="99bda-111">GetReferenceValueFromGCHandle, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="99bda-112">Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma dojście do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="99bda-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="99bda-113">GetThreadForTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="99bda-114">Pobiera wątek, na którym wykonywane jest zadanie o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="99bda-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="99bda-115">GetVersion — Metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="99bda-116">Pobiera wersję środowiska CLR, na którym jest uruchomiony debugowany proces.</span><span class="sxs-lookup"><span data-stu-id="99bda-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="99bda-117">SetDesiredNGENCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="99bda-118">Ustawia flagi wymagane przez kompilator just-in-Time (JIT) do załadowania obrazu do debugowanego procesu.</span><span class="sxs-lookup"><span data-stu-id="99bda-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="99bda-119">SetUnmanagedBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="99bda-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="99bda-120">Ustawia niezarządzany punkt przerwania w określonym przesunięciu obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="99bda-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99bda-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99bda-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99bda-122">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="99bda-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bda-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="99bda-123">Requirements</span></span>  
 <span data-ttu-id="99bda-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99bda-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bda-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="99bda-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99bda-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="99bda-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99bda-127">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99bda-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bda-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99bda-128">See also</span></span>

- [<span data-ttu-id="99bda-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="99bda-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
