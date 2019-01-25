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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff819ab67b258dbc7b5cec937863753852b1fcc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629322"
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a><span data-ttu-id="8d368-102">ICorProfilerCallback::ModuleAttachedToAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d368-102">ICorProfilerCallback::ModuleAttachedToAssembly Method</span></span>
<span data-ttu-id="8d368-103">Powiadamia program profilujący, że moduł jest dołączany do własnego zestawu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="8d368-103">Notifies the profiler that a module is being attached to its parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d368-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d368-104">Syntax</span></span>  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d368-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d368-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="8d368-106">[in] Identyfikator modułu, który jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="8d368-106">[in] The ID of the module that is being attached.</span></span>  
  
 `AssemblyId`  
 <span data-ttu-id="8d368-107">[in] Identyfikator zestawu nadrzędnego, do której jest dołączony modułu.</span><span class="sxs-lookup"><span data-stu-id="8d368-107">[in] The ID of the parent assembly to which the module is attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d368-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d368-108">Remarks</span></span>  
 <span data-ttu-id="8d368-109">Moduł może zostać załadowany przy użyciu tabeli adresów importowania (IAT) za pomocą wywołania `LoadLibrary`, lub za pomocą odwołania metadanych.</span><span class="sxs-lookup"><span data-stu-id="8d368-109">A module can be loaded through an import address table (IAT), through a call to `LoadLibrary`, or through a metadata reference.</span></span> <span data-ttu-id="8d368-110">W wyniku wspólnej ładujący środowisko uruchomieniowe (języka wspólnego CLR) języka ma wiele ścieżek kodu do określania zestawu, w którym są przechowywane w module.</span><span class="sxs-lookup"><span data-stu-id="8d368-110">As a result, the common language runtime (CLR) loader has multiple code paths for determining the assembly in which a module lives.</span></span> <span data-ttu-id="8d368-111">W związku z tym, istnieje możliwość, że po [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) jest wywoływana, moduł nie wie, jakiego zestawu znajduje się w i uzyskiwanie Identyfikatora zestawu nadrzędnego nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="8d368-111">Therefore, it is possible that after [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) is called, the module does not know what assembly it is in and getting the parent assembly ID is not possible.</span></span> <span data-ttu-id="8d368-112">`ModuleAttachedToAssembly` Metoda jest wywoływana, gdy moduł jest dołączony do zestawu nadrzędnej i jej zestawu nadrzędny można uzyskać Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8d368-112">The `ModuleAttachedToAssembly` method is called when the module is attached to its parent assembly and its parent assembly ID can be obtained.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d368-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d368-113">Requirements</span></span>  
 <span data-ttu-id="8d368-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d368-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d368-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d368-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d368-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d368-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d368-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d368-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d368-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d368-118">See also</span></span>
- [<span data-ttu-id="8d368-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d368-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
