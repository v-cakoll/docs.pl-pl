---
title: StackSnapshotCallback — Funkcja
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6140ecda1d12c26e1936daee4eaad11cbd9b6ba4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781223"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="b1c03-102">StackSnapshotCallback — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b1c03-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="b1c03-103">Dostarcza informacji na temat każdej zarządzanej ramki i każde uruchomienie niezarządzanych ramek na stosie podczas przeszukiwania stosu jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b1c03-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1c03-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1c03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1c03-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="b1c03-106">[in] Jeśli ta wartość wynosi zero, to wywołanie zwrotne jest uruchomieniu ramek niezarządzane; w przeciwnym razie jest to identyfikator funkcji zarządzanej i jest to wywołanie zwrotne ramki zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b1c03-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="b1c03-107">[in] Wartość wskaźnika instrukcji kodu natywnego w ramce.</span><span class="sxs-lookup"><span data-stu-id="b1c03-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="b1c03-108">[in] A `COR_PRF_FRAME_INFO` wartość, która odwołuje się do informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="b1c03-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="b1c03-109">Ta wartość jest prawidłowa do stosowania tylko podczas tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b1c03-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b1c03-110">[in] Rozmiar `CONTEXT` struktury, która odwołuje się do niej `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="b1c03-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="b1c03-111">[in] Wskaźnik do systemu Win32 `CONTEXT` strukturę, która reprezentuje stan procesora CPU dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="b1c03-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="b1c03-112">`context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT przekazano `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="b1c03-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="b1c03-113">[in] Wskaźnik do danych klienta, która jest przekazywana bezpośrednio z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="b1c03-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1c03-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1c03-114">Remarks</span></span>  
 <span data-ttu-id="b1c03-115">`StackSnapshotCallback` Funkcji jest implementowany przez twórcę profilera.</span><span class="sxs-lookup"><span data-stu-id="b1c03-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="b1c03-116">Należy ograniczyć złożoność pracy wykonanej w `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="b1c03-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="b1c03-117">Na przykład w przypadku korzystania z `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny, wątek docelowy może być utrzymywanie blokad.</span><span class="sxs-lookup"><span data-stu-id="b1c03-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="b1c03-118">Jeśli kodu w ramach `StackSnapshotCallback` wymaga tych samych blokad, zakleszczeń może nastąpić.</span><span class="sxs-lookup"><span data-stu-id="b1c03-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="b1c03-119">`ICorProfilerInfo2::DoStackSnapshot` Wywołania metody `StackSnapshotCallback` funkcję jeden raz na klatkę zarządzanych lub raz na przebieg niezarządzanych ramek.</span><span class="sxs-lookup"><span data-stu-id="b1c03-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="b1c03-120">Jeśli `StackSnapshotCallback` jest wywoływana dla przebiegu niezarządzanych ramek, profiler może użyć kontekstu rejestru (wskazywanym przez `context` parametr) aby wykonać swoje własne niezarządzane stosów.</span><span class="sxs-lookup"><span data-stu-id="b1c03-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="b1c03-121">W tym przypadku Win32 `CONTEXT` struktury reprezentuje stan procesora CPU dla najbardziej niedawno wypychanie ramki w ramach wykonywania niezarządzanych ramek.</span><span class="sxs-lookup"><span data-stu-id="b1c03-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="b1c03-122">Mimo że Win32 `CONTEXT` struktura zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartości rejestru wskaźnik stosu, rejestr wskaźnika ramki, rejestr wskaźnika instrukcji i nieulotnej, (które zachowane) rejestruje liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="b1c03-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c03-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1c03-123">Requirements</span></span>  
 <span data-ttu-id="b1c03-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c03-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c03-125">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b1c03-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b1c03-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c03-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c03-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c03-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c03-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1c03-128">See also</span></span>

- [<span data-ttu-id="b1c03-129">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="b1c03-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="b1c03-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="b1c03-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
