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
ms.openlocfilehash: 0e3e9da3db71d3e24b2a60ff032a631680055b88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795277"
---
# <a name="asm_cache_flags-enumeration"></a><span data-ttu-id="b12c0-102">ASM_CACHE_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b12c0-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="b12c0-103">Wskazuje źródło zestawu, który jest reprezentowany przez [IAssemblyCacheItem](iassemblycacheitem-interface.md) w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b12c0-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b12c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b12c0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b12c0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b12c0-105">Members</span></span>  
  
|<span data-ttu-id="b12c0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b12c0-106">Member</span></span>|<span data-ttu-id="b12c0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b12c0-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="b12c0-108">Wylicza pamięć podręczną wstępnie skompilowanych zestawów przy użyciu programu Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="b12c0-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="b12c0-109">Wylicza globalną pamięć podręczną zestawów.</span><span class="sxs-lookup"><span data-stu-id="b12c0-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="b12c0-110">Wylicza zestawy, które zostały pobrane na żądanie lub które zostały skopiowane w tle.</span><span class="sxs-lookup"><span data-stu-id="b12c0-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="b12c0-111">Wskazuje, że funkcja [GetCachePath —](getcachepath-function.md) powinna zwracać ścieżkę do globalnej pamięci podręcznej zestawów dla środowiska uruchomieniowego języka wspólnego (CLR) w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="b12c0-111">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="b12c0-112">Znaczenie tylko w kontekście wywołania do [GetCachePath —](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="b12c0-112">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="b12c0-113">Wskazuje, że funkcja [GetCachePath —](getcachepath-function.md) powinna zwracać ścieżkę do globalnej pamięci podręcznej zestawów dla środowiska CLR w wersji 4.</span><span class="sxs-lookup"><span data-stu-id="b12c0-113">Indicates that the [GetCachePath](getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="b12c0-114">Znaczenie tylko w kontekście wywołania do [GetCachePath —](getcachepath-function.md).</span><span class="sxs-lookup"><span data-stu-id="b12c0-114">Meaningful only in the context of a call to [GetCachePath](getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b12c0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b12c0-115">Requirements</span></span>  
 <span data-ttu-id="b12c0-116">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b12c0-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b12c0-117">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b12c0-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b12c0-118">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b12c0-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b12c0-119">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b12c0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b12c0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b12c0-120">See also</span></span>

- [<span data-ttu-id="b12c0-121">GetCachePath, funkcja</span><span class="sxs-lookup"><span data-stu-id="b12c0-121">GetCachePath Function</span></span>](getcachepath-function.md)
- [<span data-ttu-id="b12c0-122">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="b12c0-122">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
- [<span data-ttu-id="b12c0-123">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="b12c0-123">Fusion Enumerations</span></span>](fusion-enumerations.md)
