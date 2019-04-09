---
title: COR_PRF_GC_REASON — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf97f25b1adc30b173fcd81812a4b197915cdd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196947"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="a1e3f-102">COR_PRF_GC_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a1e3f-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="a1e3f-103">Wskazuje powód, że odbywa się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a1e3f-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e3f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1e3f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="a1e3f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a1e3f-105">Members</span></span>  
  
|<span data-ttu-id="a1e3f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a1e3f-106">Member</span></span>|<span data-ttu-id="a1e3f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a1e3f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="a1e3f-108">Wyrzucanie elementów bezużytecznych zostało wywołane przez <xref:System.GC.Collect%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a1e3f-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="a1e3f-109">Przyczyną jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="a1e3f-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1e3f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1e3f-110">Requirements</span></span>  
 <span data-ttu-id="a1e3f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e3f-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1e3f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1e3f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1e3f-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a1e3f-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a1e3f-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1e3f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1e3f-115">See also</span></span>

- [<span data-ttu-id="a1e3f-116">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a1e3f-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
