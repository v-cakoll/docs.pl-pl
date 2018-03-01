---
title: "ASM_CACHE_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 87dce9a2daf7067409d78a9f389695b6b01f23c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="43a12-102">ASM_CACHE_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="43a12-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="43a12-103">Wskazuje źródło zestawu, który jest reprezentowana przez [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="43a12-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43a12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43a12-104">Syntax</span></span>  
  
```  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="43a12-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="43a12-105">Members</span></span>  
  
|<span data-ttu-id="43a12-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="43a12-106">Member</span></span>|<span data-ttu-id="43a12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="43a12-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="43a12-108">Wylicza pamięci podręcznej w zestawach wstępnie skompilowanych przy użyciu Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="43a12-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="43a12-109">Wylicza globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="43a12-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="43a12-110">Wylicza zestawy, które zostały pobrane na żądanie lub które zostały skopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="43a12-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="43a12-111">Oznacza to, że [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżka do pamięci podręcznej GAC środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="43a12-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="43a12-112">Znaczenie tylko w kontekście wywołania [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="43a12-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="43a12-113">Oznacza to, że [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) funkcja powinna zwrócić ścieżki globalnej pamięci podręcznej zestawów dla CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="43a12-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="43a12-114">Znaczenie tylko w kontekście wywołania [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="43a12-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="43a12-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43a12-115">Requirements</span></span>  
 <span data-ttu-id="43a12-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43a12-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43a12-117">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="43a12-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="43a12-118">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43a12-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43a12-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43a12-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a12-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43a12-120">See Also</span></span>  
 [<span data-ttu-id="43a12-121">GetCachePath, funkcja</span><span class="sxs-lookup"><span data-stu-id="43a12-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 [<span data-ttu-id="43a12-122">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="43a12-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 [<span data-ttu-id="43a12-123">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="43a12-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
