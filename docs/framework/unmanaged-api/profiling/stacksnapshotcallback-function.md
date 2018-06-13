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
ms.openlocfilehash: 78fdcb69e73bc7238972d1a6ffb37b5ba91c7953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459088"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="e909a-102">StackSnapshotCallback — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e909a-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="e909a-103">Zawiera informacje o każdej ramce zarządzanych i każdym uruchomieniu niezarządzane ramek na stosie podczas przeszukiwania stosu, który jest inicjowane przez profiler [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e909a-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e909a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e909a-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e909a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e909a-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="e909a-106">[in] Jeśli ta wartość wynosi zero, to wywołanie zwrotne jest dla przebiegu niezarządzane ramek; w przeciwnym razie jest identyfikator zarządzanego funkcji i jest to wywołanie zwrotne dla ramki zarządzane.</span><span class="sxs-lookup"><span data-stu-id="e909a-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="e909a-107">[in] Wartość wskaźnika instrukcji kodu macierzystego w ramce.</span><span class="sxs-lookup"><span data-stu-id="e909a-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="e909a-108">[in] A `COR_PRF_FRAME_INFO` wartość, która odwołuje się do informacji na temat ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="e909a-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="e909a-109">Ta wartość jest prawidłowa do stosowania tylko podczas tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e909a-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e909a-110">[in] Rozmiar `CONTEXT` struktury, która odwołuje się do niego `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="e909a-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="e909a-111">[in] Wskaźnik do Win32 `CONTEXT` strukturę, która reprezentuje stan procesora CPU dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="e909a-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="e909a-112">`context` Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przekazana `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="e909a-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="e909a-113">[in] Wskaźnik do danych klienta, który jest przekazywane bezpośrednio z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="e909a-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e909a-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e909a-114">Remarks</span></span>  
 <span data-ttu-id="e909a-115">`StackSnapshotCallback` Funkcji jest implementowany przez twórcę profilera.</span><span class="sxs-lookup"><span data-stu-id="e909a-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="e909a-116">Należy ograniczyć złożoność pracować `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="e909a-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="e909a-117">Na przykład w przypadku korzystania z `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być blokują.</span><span class="sxs-lookup"><span data-stu-id="e909a-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="e909a-118">Jeśli kod w `StackSnapshotCallback` wymaga tego samego blokad, może nastąpić zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="e909a-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="e909a-119">`ICorProfilerInfo2::DoStackSnapshot` Wywołania metody `StackSnapshotCallback` funkcja raz na klatkę zarządzanego, lub raz na przebieg niezarządzane ramek.</span><span class="sxs-lookup"><span data-stu-id="e909a-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="e909a-120">Jeśli `StackSnapshotCallback` nosi nazwę dla przebiegu niezarządzane ramek, profiler może używać kontekstu rejestru (odwołuje `context` parametru) do wykonania własną stosów niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="e909a-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="e909a-121">W tym przypadku Win32 `CONTEXT` struktury reprezentuje stan Procesora najbardziej ostatnio wciśnięcia ramki w ramach Uruchom niezarządzane ramki.</span><span class="sxs-lookup"><span data-stu-id="e909a-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="e909a-122">Mimo że Win32 `CONTEXT` struktura zawiera wartości dla wszystkich rejestrów, należy polegać wyłącznie na wartości rejestru wskaźnik stosu, rejestr wskaźnika ramki, rejestr wskaźnika instrukcji i nieulotnej, (tj. zachowane) rejestruje liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="e909a-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e909a-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e909a-123">Requirements</span></span>  
 <span data-ttu-id="e909a-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e909a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e909a-125">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e909a-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e909a-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e909a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e909a-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e909a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e909a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e909a-128">See Also</span></span>  
 [<span data-ttu-id="e909a-129">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="e909a-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="e909a-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="e909a-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
