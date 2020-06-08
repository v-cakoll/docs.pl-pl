---
title: ICorProfilerCallback::ModuleAttachedToAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleAttachedToAssembly
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type:
- apiref
ms.openlocfilehash: 4f494919d11e0f979cf1964c08106fbb9b9ed20b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503396"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="b0628-102">ICorProfilerCallback::ModuleAttachedToAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="b0628-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="b0628-103">Powiadamia program profilujący, że moduł jest dołączony do jego zestawu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b0628-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0628-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0628-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0628-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b0628-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="b0628-106">podczas Identyfikator dołączanego modułu.</span><span class="sxs-lookup"><span data-stu-id="b0628-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="b0628-107">podczas Identyfikator zestawu nadrzędnego, do którego jest dołączony moduł.</span><span class="sxs-lookup"><span data-stu-id="b0628-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0628-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0628-108">Remarks</span></span>  
 <span data-ttu-id="b0628-109">Moduł może zostać załadowany za pomocą tabeli adresów importu (IAT), przez wywołanie do `LoadLibrary` lub przez odwołanie do metadanych.</span><span class="sxs-lookup"><span data-stu-id="b0628-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="b0628-110">W związku z tym moduł ładujący środowisko uruchomieniowe języka wspólnego (CLR) ma wiele ścieżek kodu do określenia zestawu, w którym przebywa moduł.</span><span class="sxs-lookup"><span data-stu-id="b0628-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="b0628-111">W związku z tym jest możliwe, że po wywołaniu [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) moduł nie wie, w jakim zestawie znajduje się i nie jest możliwe uzyskanie identyfikatora zestawu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b0628-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="b0628-112">`ModuleAttachedToAssembly`Metoda jest wywoływana, gdy moduł jest dołączony do jego zestawu nadrzędnego i można uzyskać jego identyfikator zestawu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b0628-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0628-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0628-113">Requirements</span></span>  
 <span data-ttu-id="b0628-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0628-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0628-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0628-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0628-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b0628-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0628-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0628-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0628-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0628-118">See also</span></span>

- [<span data-ttu-id="b0628-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b0628-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
