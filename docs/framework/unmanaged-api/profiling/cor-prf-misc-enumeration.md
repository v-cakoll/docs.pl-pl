---
title: "COR_PRF_MISC — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_MISC
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_MISC
helpviewer_keywords: COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75e740a6ca17135a3de2e945e205f4581b2f32e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="a48a7-102">COR_PRF_MISC — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a48a7-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="a48a7-103">Zawiera stałe wartości, które określają specjalne identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="a48a7-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a48a7-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="a48a7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a48a7-105">Members</span></span>  
  
|<span data-ttu-id="a48a7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a48a7-106">Member</span></span>|<span data-ttu-id="a48a7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a48a7-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="a48a7-108">Domyślny identyfikator używany przez [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) modułów, które jeszcze nie został dołączony do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a48a7-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="a48a7-109">Identyfikator klasy domyślne stałe globalne, które nie należą do klasy.</span><span class="sxs-lookup"><span data-stu-id="a48a7-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="a48a7-110">Domyślny identyfikator modułu dla obiektów globalnych, które nie należą do modułu.</span><span class="sxs-lookup"><span data-stu-id="a48a7-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a48a7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a48a7-111">Requirements</span></span>  
 <span data-ttu-id="a48a7-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a48a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a48a7-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a48a7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a48a7-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a48a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a48a7-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a48a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48a7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a48a7-116">See Also</span></span>  
 [<span data-ttu-id="a48a7-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a48a7-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
