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
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427081"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="27e3f-102">StackSnapshotCallback — Funkcja</span><span class="sxs-lookup"><span data-stu-id="27e3f-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="27e3f-103">Zapewnia profilerowi informacje o każdej zarządzanej ramce i każdym uruchomieniu niezarządzanych ramek na stosie podczas przechodzenia stosu, który jest inicjowany przez [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27e3f-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27e3f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="27e3f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27e3f-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="27e3f-106">podczas Jeśli ta wartość jest równa zero, to wywołanie zwrotne dotyczy przebiegu ramek niezarządzanych; w przeciwnym razie jest to identyfikator funkcji zarządzanej, a to wywołanie zwrotne dotyczy ramki zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="27e3f-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="27e3f-107">podczas Wartość wskaźnika instrukcji kodu natywnego w ramce.</span><span class="sxs-lookup"><span data-stu-id="27e3f-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="27e3f-108">podczas Wartość `COR_PRF_FRAME_INFO`, która odwołuje się do informacji o ramce stosu.</span><span class="sxs-lookup"><span data-stu-id="27e3f-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="27e3f-109">Ta wartość jest prawidłowa do użycia tylko w trakcie tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="27e3f-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="27e3f-110">podczas Rozmiar struktury `CONTEXT`, do której odwołuje się parametr `context`.</span><span class="sxs-lookup"><span data-stu-id="27e3f-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="27e3f-111">podczas Wskaźnik do struktury `CONTEXT` Win32, który reprezentuje stan procesora CPU dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="27e3f-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="27e3f-112">Parametr `context` jest prawidłowy tylko wtedy, gdy flaga COR_PRF_SNAPSHOT_CONTEXT została przeniesiona w `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="27e3f-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="27e3f-113">podczas Wskaźnik do danych klienta, który jest przenoszona bezpośrednio przez z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="27e3f-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27e3f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27e3f-114">Remarks</span></span>  
 <span data-ttu-id="27e3f-115">Funkcja `StackSnapshotCallback` jest implementowana przez moduł zapisujący profilera.</span><span class="sxs-lookup"><span data-stu-id="27e3f-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="27e3f-116">Należy ograniczyć złożoność pracy wykonywanej w `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="27e3f-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="27e3f-117">Na przykład w przypadku używania `ICorProfilerInfo2::DoStackSnapshot` w sposób asynchroniczny wątek docelowy może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="27e3f-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="27e3f-118">Jeśli kod w `StackSnapshotCallback` wymaga tych samych blokad, może nastąpić zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="27e3f-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="27e3f-119">Metoda `ICorProfilerInfo2::DoStackSnapshot` wywołuje funkcję `StackSnapshotCallback` raz dla każdej zarządzanej ramki lub raz na uruchomienie niezarządzanych ramek.</span><span class="sxs-lookup"><span data-stu-id="27e3f-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="27e3f-120">Jeśli `StackSnapshotCallback` jest wywoływana w przypadku uruchamiania ramek niezarządzanych, profiler może użyć kontekstu rejestru (przywoływanego przez parametr `context`) do wykonania własnego przeszukiwania niezarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="27e3f-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="27e3f-121">W takim przypadku struktura `CONTEXT` Win32 reprezentuje stan procesora dla ostatnio wypchniętej ramki w ramach przebiegu ramek niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="27e3f-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="27e3f-122">Mimo że struktura `CONTEXT` Win32 zawiera wartości dla wszystkich rejestrów, należy polegać tylko na wartościach rejestru wskaźnika stosu, rejestracji wskaźnika ramki, rejestru wskaźnika instrukcji i nietrwałych (przechowywanych) rejestrów liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="27e3f-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27e3f-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27e3f-123">Requirements</span></span>  
 <span data-ttu-id="27e3f-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27e3f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27e3f-125">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="27e3f-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="27e3f-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="27e3f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27e3f-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27e3f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e3f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27e3f-128">See also</span></span>

- [<span data-ttu-id="27e3f-129">DoStackSnapshot, metoda</span><span class="sxs-lookup"><span data-stu-id="27e3f-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="27e3f-130">Profilowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="27e3f-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
