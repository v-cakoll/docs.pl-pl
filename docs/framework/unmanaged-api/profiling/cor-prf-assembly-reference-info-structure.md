---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867337"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="b511e-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="b511e-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="b511e-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b511e-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b511e-104">Zapewnia środowisko uruchomieniowe języka wspólnego z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b511e-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b511e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b511e-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b511e-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b511e-106">Members</span></span>  
  
|<span data-ttu-id="b511e-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b511e-107">Member</span></span>|<span data-ttu-id="b511e-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b511e-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="b511e-109">Wskaźnik do klucza publicznego lub tokenu zestawu.</span><span class="sxs-lookup"><span data-stu-id="b511e-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="b511e-110">Liczba bajtów w kluczu publicznym lub tokenie.</span><span class="sxs-lookup"><span data-stu-id="b511e-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="b511e-111">Nazwa zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b511e-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="b511e-112">Wskaźnik do metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="b511e-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="b511e-113">Wskaźnik do binarnego dużego obiektu typu hash (BLOB).</span><span class="sxs-lookup"><span data-stu-id="b511e-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="b511e-114">Liczba bajtów w obiekcie BLOB mieszania.</span><span class="sxs-lookup"><span data-stu-id="b511e-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="b511e-115">Flagi zestawu.</span><span class="sxs-lookup"><span data-stu-id="b511e-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b511e-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b511e-116">Remarks</span></span>  
 <span data-ttu-id="b511e-117">Struktura `COR_PRF_EX_CLAUSE_INFO` jest wypełniana przez profiler, gdy deklaruje dodatkowe odwołania do zestawu, że środowisko uruchomieniowe języka wspólnego należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b511e-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="b511e-118">Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do obiektu interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) do tej metody.</span><span class="sxs-lookup"><span data-stu-id="b511e-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="b511e-119">Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b511e-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b511e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b511e-120">Requirements</span></span>  
 <span data-ttu-id="b511e-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b511e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b511e-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b511e-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b511e-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b511e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b511e-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b511e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b511e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b511e-125">See also</span></span>

- [<span data-ttu-id="b511e-126">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="b511e-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="b511e-127">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="b511e-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="b511e-128">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="b511e-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
