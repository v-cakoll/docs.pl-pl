---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fa1cc05ee583cf1bd59235fcd9821d1c92d21f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101435"
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="b400a-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="b400a-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="b400a-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b400a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b400a-104">Udostępnia środowisko uruchomieniowe języka wspólnego z informacjami dotyczącymi odwołania do zestawu, należy rozważyć, podczas przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b400a-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b400a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b400a-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b400a-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b400a-106">Members</span></span>  
  
|<span data-ttu-id="b400a-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b400a-107">Member</span></span>|<span data-ttu-id="b400a-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b400a-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="b400a-109">Wskaźnik do publicznego klucza lub tokenu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b400a-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="b400a-110">Liczba bajtów w tokenu lub klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="b400a-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="b400a-111">Nazwa zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b400a-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="b400a-112">Wskaźnik do metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="b400a-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="b400a-113">Wskaźnik do wyznaczania wartości skrótu duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b400a-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="b400a-114">Liczba bajtów skrótu obiektu BLOB.</span><span class="sxs-lookup"><span data-stu-id="b400a-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="b400a-115">Flagi zestawu.</span><span class="sxs-lookup"><span data-stu-id="b400a-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b400a-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b400a-116">Remarks</span></span>  
 <span data-ttu-id="b400a-117">`COR_PRF_EX_CLAUSE_INFO` Struktury jest wypełniana przez profiler, gdy deklaruje odwołań do zestawu dodatkowe środowiska uruchomieniowego języka wspólnego należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b400a-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="b400a-118">Jeśli program profilujący rejestruje [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego, środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu do załadowania, wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody.</span><span class="sxs-lookup"><span data-stu-id="b400a-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="b400a-119">Program profilujący może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego, firma planuje odwoływać się z zestawu określonego w [ ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b400a-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b400a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b400a-120">Requirements</span></span>  
 <span data-ttu-id="b400a-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b400a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b400a-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b400a-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b400a-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b400a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b400a-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b400a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b400a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b400a-125">See also</span></span>

- [<span data-ttu-id="b400a-126">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="b400a-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="b400a-127">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="b400a-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="b400a-128">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="b400a-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
