---
title: Metoda ICorProfilerCallback6::GetAssemblyReferences
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2e80d6d8207a869d43beb46cc9448bdd86dfec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="2069e-102">Metoda ICorProfilerCallback6::GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="2069e-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="2069e-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2069e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2069e-104">Powiadamia profilera, że zestaw w bardzo wczesny ładuje etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2069e-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2069e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2069e-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2069e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2069e-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="2069e-107">[in] Ścieżka i nazwa zestawu, którego metadane zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="2069e-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="2069e-108">[in] Wskaźnik do adresu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interfejsu, który określa zestaw odwołuje się do dodania.</span><span class="sxs-lookup"><span data-stu-id="2069e-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2069e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2069e-109">Return Value</span></span>  
 <span data-ttu-id="2069e-110">Wartości zwracane z tego wywołania zwrotnego są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2069e-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2069e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2069e-111">Remarks</span></span>  
 <span data-ttu-id="2069e-112">To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi Maska zdarzenia podczas wywoływania metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2069e-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="2069e-113">Jeśli rejestruje profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego środowiska uruchomieniowego przekazuje ścieżkę i nazwę zestawu do załadowania wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody.</span><span class="sxs-lookup"><span data-stu-id="2069e-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="2069e-114">Profiler może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego planuje odwoływać się z zestawu określonego w `GetAssemblyReferences` Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="2069e-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="2069e-115">Użyj `GetAssemblyReferences` wywołania zwrotnego tylko wtedy, gdy profilera do zmodyfikowania metadanych zestawu można dodać odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="2069e-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="2069e-116">(Ale należy pamiętać, że rzeczywiste zmiany metadanych zestawu jest wykonywane w [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)metody wywołania zwrotnego.) Profiler powinien implementować `GetAssemblyReferences` metody wywołania zwrotnego informują środowisko uruchomieniowe języka wspólnego (CLR) o tym, że odwołania do zestawów zostaną dodane po załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="2069e-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="2069e-117">Pomaga to zapewnić, że zestaw udostępniania decyzje przez środowisko CLR na tym etapie wczesne ważność chociaż profilera planuje później zmodyfikować odwołania do zestawu metadanych.</span><span class="sxs-lookup"><span data-stu-id="2069e-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="2069e-118">To uniknąć niektórych wystąpień, w których profilera zmiany metadanych powodują `SECURITY_E_INCOMPATIBLE_SHARE` błędu.</span><span class="sxs-lookup"><span data-stu-id="2069e-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="2069e-119">Używa profilera [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt udostępniany przez tę metodę, aby dodać odwołania do zestawów do walkera zamknięcia odwołanie do zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="2069e-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="2069e-120">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) należy go używać tylko z wewnątrz tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2069e-120">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="2069e-121">Wywołuje się [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodę z tego wywołania zwrotnego nie powodują w metadanych zmodyfikowany, ale tylko w przeszukiwania zamknięcia odwołanie do zestawu zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="2069e-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="2069e-122">Profiler nadal będą musieli używać [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) obiekt, aby jawnie dodać odwołania do zestawów z poziomu [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego dla odwołujących się zestaw, nawet jeśli implementuje `GetAssemblyReferences` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2069e-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="2069e-123">Profiler powinna być przygotowana do odbierania zduplikowane wywołania tego wywołania zwrotnego dla tego samego zestawu i powinny odpowiadać tak samo dla każdego wywołania zduplikowane (poprzez ten sam zestaw [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) wywołania).</span><span class="sxs-lookup"><span data-stu-id="2069e-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2069e-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2069e-124">Requirements</span></span>  
 <span data-ttu-id="2069e-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2069e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2069e-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2069e-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2069e-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2069e-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2069e-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2069e-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2069e-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2069e-129">See Also</span></span>  
 [<span data-ttu-id="2069e-130">ICorProfilerCallback6, interfejs</span><span class="sxs-lookup"><span data-stu-id="2069e-130">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [<span data-ttu-id="2069e-131">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="2069e-131">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="2069e-132">COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="2069e-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [<span data-ttu-id="2069e-133">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="2069e-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
