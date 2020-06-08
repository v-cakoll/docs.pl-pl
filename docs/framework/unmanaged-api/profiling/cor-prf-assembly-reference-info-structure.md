---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 861b31e5621e9a7b40403d249c6a5c8c4ac25db8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501043"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="43b95-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="43b95-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="43b95-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="43b95-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="43b95-104">Zapewnia środowisko uruchomieniowe języka wspólnego z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="43b95-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b95-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b95-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="43b95-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="43b95-106">Members</span></span>  
  
|<span data-ttu-id="43b95-107">Członek</span><span class="sxs-lookup"><span data-stu-id="43b95-107">Member</span></span>|<span data-ttu-id="43b95-108">Opis</span><span class="sxs-lookup"><span data-stu-id="43b95-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="43b95-109">Wskaźnik do klucza publicznego lub tokenu zestawu.</span><span class="sxs-lookup"><span data-stu-id="43b95-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="43b95-110">Liczba bajtów w kluczu publicznym lub tokenie.</span><span class="sxs-lookup"><span data-stu-id="43b95-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="43b95-111">Nazwa zestawu, do którego istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="43b95-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="43b95-112">Wskaźnik do metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="43b95-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="43b95-113">Wskaźnik do binarnego dużego obiektu typu hash (BLOB).</span><span class="sxs-lookup"><span data-stu-id="43b95-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="43b95-114">Liczba bajtów w obiekcie BLOB mieszania.</span><span class="sxs-lookup"><span data-stu-id="43b95-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="43b95-115">Flagi zestawu.</span><span class="sxs-lookup"><span data-stu-id="43b95-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43b95-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b95-116">Remarks</span></span>  
 <span data-ttu-id="43b95-117">`COR_PRF_EX_CLAUSE_INFO`Struktura jest wypełniana przez profiler, gdy deklaruje dodatkowe odwołania do zestawu, że środowisko uruchomieniowe języka wspólnego należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="43b95-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="43b95-118">Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do obiektu interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) do tej metody.</span><span class="sxs-lookup"><span data-stu-id="43b95-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="43b95-119">Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiektem dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="43b95-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43b95-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43b95-120">Requirements</span></span>  
 <span data-ttu-id="43b95-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43b95-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43b95-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="43b95-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43b95-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="43b95-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43b95-124">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43b95-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b95-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43b95-125">See also</span></span>

- [<span data-ttu-id="43b95-126">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="43b95-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="43b95-127">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="43b95-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="43b95-128">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="43b95-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
