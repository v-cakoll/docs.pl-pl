---
title: COR_PRF_GC_ROOT_KIND — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0f5b12825c9a348cd16eed9f5be0f41e03c367c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corprfgcrootkind-enumeration"></a><span data-ttu-id="dedd7-102">COR_PRF_GC_ROOT_KIND — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dedd7-102">COR_PRF_GC_ROOT_KIND Enumeration</span></span>
<span data-ttu-id="dedd7-103">Określa rodzaj operacji wyrzucania elementów kolekcji głównego, który jest udostępniany przez [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="dedd7-103">Indicates the kind of garbage collection root that is exposed by the [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dedd7-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a><span data-ttu-id="dedd7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="dedd7-105">Members</span></span>  
  
|<span data-ttu-id="dedd7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="dedd7-106">Member</span></span>|<span data-ttu-id="dedd7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dedd7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|<span data-ttu-id="dedd7-108">Główny jest zmienna na stosie.</span><span class="sxs-lookup"><span data-stu-id="dedd7-108">The root is a variable on the stack.</span></span>|  
|`COR_PRF_GC_ROOT_FINALIZER`|<span data-ttu-id="dedd7-109">Katalog główny to pozycja w kolejce finalizatora.</span><span class="sxs-lookup"><span data-stu-id="dedd7-109">The root is an entry in the finalizer queue.</span></span>|  
|`COR_PRF_GC_ROOT_HANDLE`|<span data-ttu-id="dedd7-110">Główny jest dojście kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="dedd7-110">The root is a garbage collection handle.</span></span>|  
|`COR_PRF_GC_ROOT_OTHER`|<span data-ttu-id="dedd7-111">Rodzaj elementu głównego jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="dedd7-111">The kind of root is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dedd7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dedd7-112">Requirements</span></span>  
 <span data-ttu-id="dedd7-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dedd7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedd7-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dedd7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dedd7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dedd7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dedd7-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedd7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedd7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dedd7-117">See Also</span></span>  
 [<span data-ttu-id="dedd7-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="dedd7-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
