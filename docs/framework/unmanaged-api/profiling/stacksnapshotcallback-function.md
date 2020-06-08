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
ms.openlocfilehash: a0f5316900dedc6c8983f9e670f60767ed783a40
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493997"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="0c83b-102">StackSnapshotCallback — Funkcja</span><span class="sxs-lookup"><span data-stu-id="0c83b-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="0c83b-103">Zapewnia profilerowi informacje o każdej zarządzanej ramce i każdym uruchomieniu niezarządzanych ramek na stosie podczas przechodzenia stosu, który jest inicjowany przez [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0c83b-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c83b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c83b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0c83b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c83b-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="0c83b-106">podczas Jeśli ta wartość jest równa zero, to wywołanie zwrotne dotyczy przebiegu ramek niezarządzanych; w przeciwnym razie jest to identyfikator funkcji zarządzanej, a to wywołanie zwrotne dotyczy ramki zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0c83b-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="0c83b-107">podczas Wartość wskaźnika instrukcji kodu natywnego w ramce.</span><span class="sxs-lookup"><span data-stu-id="0c83b-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="0c83b-108">podczas `COR_PRF_FRAME_INFO`Wartość, która odwołuje się do informacji o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="0c83b-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="0c83b-109">Ta wartość jest prawidłowa do użycia tylko w trakcie tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0c83b-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="0c83b-110">podczas Rozmiar `CONTEXT` struktury, do której odwołuje się `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="0c83b-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="0c83b-111">podczas Wskaźnik do `CONTEXT` struktury Win32, który reprezentuje stan procesora CPU dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="0c83b-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="0c83b-112">`context`Parametr jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przeniesiona `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="0c83b-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="0c83b-113">podczas Wskaźnik do danych klienta, który jest przenoszona bezpośrednio przez z `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="0c83b-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c83b-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c83b-114">Remarks</span></span>  
 <span data-ttu-id="0c83b-115">`StackSnapshotCallback`Funkcja jest implementowana przez moduł zapisujący profilera.</span><span class="sxs-lookup"><span data-stu-id="0c83b-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="0c83b-116">Należy ograniczyć złożoność pracy wykonywanej w programie `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="0c83b-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="0c83b-117">Na przykład w przypadku użycia `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="0c83b-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="0c83b-118">Jeśli kod w ramach `StackSnapshotCallback` wymaga tych samych blokad, może nastąpić zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="0c83b-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="0c83b-119">`ICorProfilerInfo2::DoStackSnapshot`Metoda wywołuje `StackSnapshotCallback` funkcję jeden raz dla każdej zarządzanej ramki lub raz na uruchomienie niezarządzanych ramek.</span><span class="sxs-lookup"><span data-stu-id="0c83b-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="0c83b-120">Jeśli `StackSnapshotCallback` jest wywoływana w przypadku uruchamiania ramek niezarządzanych, profiler może użyć kontekstu rejestru (przywoływanego przez `context` parametr) do wykonania własnego przeszukiwania niezarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="0c83b-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="0c83b-121">W takim przypadku `CONTEXT` Struktura Win32 reprezentuje stan procesora dla ostatnio wypchniętej ramki w ramach przebiegu ramek niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="0c83b-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="0c83b-122">Chociaż struktura Win32 `CONTEXT` zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartościach rejestru wskaźnika stosu, rejestracji wskaźnika ramki, rejestracji wskaźnika instrukcji i nietrwałych (przechowywanych) rejestrów liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0c83b-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c83b-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c83b-123">Requirements</span></span>  
 <span data-ttu-id="0c83b-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c83b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c83b-125">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="0c83b-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0c83b-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c83b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c83b-127">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c83b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c83b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c83b-128">See also</span></span>

- [<span data-ttu-id="0c83b-129">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="0c83b-129">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="0c83b-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0c83b-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
