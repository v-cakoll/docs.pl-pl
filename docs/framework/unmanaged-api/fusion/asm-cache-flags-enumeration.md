---
title: ASM_CACHE_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b712c6ae5978e83dab085f48dd1fd572757384a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47195696"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="72fdd-102">ASM_CACHE_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="72fdd-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="72fdd-103">Wskazuje źródło zestawu, który jest reprezentowany przez [iassemblycacheitem —](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="72fdd-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72fdd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72fdd-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="72fdd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="72fdd-105">Members</span></span>  
  
|<span data-ttu-id="72fdd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="72fdd-106">Member</span></span>|<span data-ttu-id="72fdd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="72fdd-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="72fdd-108">Wylicza pamięci podręcznej zestawów, wstępnie skompilowane przy użyciu Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="72fdd-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="72fdd-109">Wylicza globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="72fdd-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="72fdd-110">Wylicza zestawy, które zostały pobrane na żądanie lub które zostały skopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="72fdd-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="72fdd-111">Oznacza to, że [getcachepath —](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżki do globalnej pamięci podręcznej, aby uzyskać środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="72fdd-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="72fdd-112">Znaczenie tylko w kontekście wywołania [getcachepath —](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="72fdd-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="72fdd-113">Oznacza to, że [getcachepath —](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżki do globalnej pamięci podręcznej dla CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="72fdd-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="72fdd-114">Znaczenie tylko w kontekście wywołania [getcachepath —](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="72fdd-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72fdd-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72fdd-115">Requirements</span></span>  
 <span data-ttu-id="72fdd-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72fdd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72fdd-117">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="72fdd-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="72fdd-118">**Biblioteka:** dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72fdd-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72fdd-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72fdd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fdd-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72fdd-120">See Also</span></span>  
 [<span data-ttu-id="72fdd-121">GetCachePath, funkcja</span><span class="sxs-lookup"><span data-stu-id="72fdd-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="72fdd-122">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="72fdd-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="72fdd-123">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="72fdd-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
