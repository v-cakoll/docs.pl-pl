---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: ac7ddeed5694ad0ae6ef3d4a11fcb1fb23755b8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123228"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="064bf-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="064bf-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="064bf-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="064bf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="064bf-104">Zapewnia środowisko uruchomieniowe języka wspólnego z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="064bf-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="064bf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="064bf-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="064bf-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="064bf-106">Members</span></span>  
  
|<span data-ttu-id="064bf-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="064bf-107">Member</span></span>|<span data-ttu-id="064bf-108">Opis</span><span class="sxs-lookup"><span data-stu-id="064bf-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="064bf-109">Wskaźnik do klucza publicznego lub tokenu zestawu.</span><span class="sxs-lookup"><span data-stu-id="064bf-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="064bf-110">Liczba bajtów w kluczu publicznym lub tokenie.</span><span class="sxs-lookup"><span data-stu-id="064bf-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="064bf-111">Nazwa zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="064bf-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="064bf-112">Wskaźnik do metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="064bf-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="064bf-113">Wskaźnik do binarnego dużego obiektu typu hash (BLOB).</span><span class="sxs-lookup"><span data-stu-id="064bf-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="064bf-114">Liczba bajtów w obiekcie BLOB mieszania.</span><span class="sxs-lookup"><span data-stu-id="064bf-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="064bf-115">Flagi zestawu.</span><span class="sxs-lookup"><span data-stu-id="064bf-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="064bf-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="064bf-116">Remarks</span></span>  
 <span data-ttu-id="064bf-117">Struktura `COR_PRF_EX_CLAUSE_INFO` jest wypełniana przez profiler, gdy deklaruje dodatkowe odwołania do zestawu, że środowisko uruchomieniowe języka wspólnego należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="064bf-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="064bf-118">Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt interfejsu do tej metody.</span><span class="sxs-lookup"><span data-stu-id="064bf-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="064bf-119">Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w [ICorProfilerCallback6:: ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)Wywołanie zwrotne GetAssemblyReferences.</span><span class="sxs-lookup"><span data-stu-id="064bf-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="064bf-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="064bf-120">Requirements</span></span>  
 <span data-ttu-id="064bf-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="064bf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="064bf-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="064bf-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="064bf-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="064bf-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="064bf-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="064bf-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="064bf-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="064bf-125">See also</span></span>

- [<span data-ttu-id="064bf-126">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="064bf-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="064bf-127">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="064bf-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="064bf-128">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="064bf-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
