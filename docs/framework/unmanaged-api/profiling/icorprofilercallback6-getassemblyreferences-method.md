---
title: Metoda ICorProfilerCallback6::GetAssemblyReferences
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 0717ef5fdb6c0447ceeb801f239be08f8cca5988
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865054"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="b5747-102">Metoda ICorProfilerCallback6::GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="b5747-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="b5747-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b5747-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b5747-104">Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b5747-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5747-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5747-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5747-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b5747-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="b5747-107">podczas Ścieżka i nazwa zestawu, którego metadane zostaną zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="b5747-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="b5747-108">podczas Wskaźnik do adresu interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) , który określa odwołania do zestawu do dodania.</span><span class="sxs-lookup"><span data-stu-id="b5747-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5747-109">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="b5747-109">Return Value</span></span>  
 <span data-ttu-id="b5747-110">Zwracane wartości z tego wywołania zwrotnego są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="b5747-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5747-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5747-111">Remarks</span></span>  
 <span data-ttu-id="b5747-112">To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b5747-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="b5747-113">Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do obiektu interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) do tej metody.</span><span class="sxs-lookup"><span data-stu-id="b5747-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="b5747-114">Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w `GetAssemblyReferences` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b5747-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="b5747-115">Użyj wywołania zwrotnego `GetAssemblyReferences` tylko wtedy, gdy profiler musi zmodyfikować metadane zestawu, aby dodać odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b5747-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="b5747-116">(Należy zauważyć, że rzeczywista modyfikacja metadanych zestawu jest wykonywana w metodzie wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md)). Profiler powinien zaimplementować metodę wywołania zwrotnego `GetAssemblyReferences`, aby poinformować środowisko uruchomieniowe języka wspólnego (CLR) o tym, że odwołania do zestawów zostaną dodane po załadowaniu modułu.</span><span class="sxs-lookup"><span data-stu-id="b5747-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="b5747-117">Pozwala to zagwarantować, że decyzje dotyczące udostępniania zestawu wykonane przez środowisko CLR w trakcie tego wczesnego etapu pozostają prawidłowe, mimo że program profilujący planuje później zmodyfikować odwołania do zestawu metadanych.</span><span class="sxs-lookup"><span data-stu-id="b5747-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="b5747-118">Może to uniknąć niektórych wystąpień, w których modyfikacje metadanych profilera powodują wystąpienie błędu `SECURITY_E_INCOMPATIBLE_SHARE`.</span><span class="sxs-lookup"><span data-stu-id="b5747-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="b5747-119">Profiler używa obiektu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) dostarczonego przez tę metodę, aby dodać odwołania do zestawu do analizatora zamknięcia odwołań do zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="b5747-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="b5747-120">Obiekt [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) powinien być używany tylko w ramach tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b5747-120">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="b5747-121">Wywołania metody [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z tego wywołania zwrotnego nie powodują zmodyfikowanych metadanych, ale tylko w zmodyfikowanym zamknięciu odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b5747-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="b5747-122">Profiler nadal będzie musiał używać obiektu [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , aby jawnie dodawać odwołania do zestawów z poziomu wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) dla zestawu, który odwołuje się, nawet jeśli implementuje wywołanie zwrotne `GetAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="b5747-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="b5747-123">Profiler powinien zostać przygotowany do odbierania zduplikowanych wywołań tego wywołania zwrotnego dla tego samego zestawu i powinien odpowiadać identycznie dla każdego takiego duplikatu wywołania (przez nadanie tego samego zestawu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="b5747-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5747-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b5747-124">Requirements</span></span>  
 <span data-ttu-id="b5747-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5747-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5747-126">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b5747-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b5747-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b5747-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5747-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5747-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5747-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5747-129">See also</span></span>

- [<span data-ttu-id="b5747-130">ICorProfilerCallback6, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5747-130">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="b5747-131">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="b5747-131">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="b5747-132">COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura</span><span class="sxs-lookup"><span data-stu-id="b5747-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="b5747-133">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b5747-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
