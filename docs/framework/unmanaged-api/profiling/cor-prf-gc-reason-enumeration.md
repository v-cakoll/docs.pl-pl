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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196947"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="ddf28-102">COR_PRF_GC_REASON — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ddf28-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="ddf28-103">Wskazuje powód, że odbywa się wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ddf28-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddf28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ddf28-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="ddf28-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ddf28-105">Members</span></span>  
  
|<span data-ttu-id="ddf28-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ddf28-106">Member</span></span>|<span data-ttu-id="ddf28-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ddf28-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="ddf28-108">Wyrzucanie elementów bezużytecznych zostało wywołane przez <xref:System.GC.Collect%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ddf28-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="ddf28-109">Przyczyną jest nieokreślona.</span><span class="sxs-lookup"><span data-stu-id="ddf28-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ddf28-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ddf28-110">Requirements</span></span>  
 <span data-ttu-id="ddf28-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddf28-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddf28-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ddf28-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ddf28-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddf28-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddf28-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddf28-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf28-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddf28-115">See also</span></span>

- [<span data-ttu-id="ddf28-116">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ddf28-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
