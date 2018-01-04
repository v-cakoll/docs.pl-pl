---
title: "COR_PRF_STATIC_TYPE — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_STATIC_TYPE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_STATIC_TYPE
helpviewer_keywords: COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76d43a620b64c771427cd30af770e70642dabe7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="a1861-102">COR_PRF_STATIC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a1861-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="a1861-103">Wskazuje, czy pole jest statyczny, a jeśli tak, statyczne jakości dotyczący pola.</span><span class="sxs-lookup"><span data-stu-id="a1861-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="a1861-104">Wartości te można łączyć, używając operacji lub wskaż, czy pole ma wiele różnych klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="a1861-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1861-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1861-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a1861-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a1861-106">Members</span></span>  
  
|<span data-ttu-id="a1861-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a1861-107">Member</span></span>|<span data-ttu-id="a1861-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a1861-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="a1861-109">Pole nie jest statyczne.</span><span class="sxs-lookup"><span data-stu-id="a1861-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="a1861-110">To pole jest statyczna domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a1861-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="a1861-111">To pole jest statyczne dla wątku.</span><span class="sxs-lookup"><span data-stu-id="a1861-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="a1861-112">To pole jest kontekstu statycznego.</span><span class="sxs-lookup"><span data-stu-id="a1861-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="a1861-113">W polu jest adres względny wirtualnych (RVA)-statycznych.</span><span class="sxs-lookup"><span data-stu-id="a1861-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1861-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1861-114">Requirements</span></span>  
 <span data-ttu-id="a1861-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1861-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1861-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1861-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1861-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1861-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1861-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1861-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1861-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1861-119">See Also</span></span>  
 [<span data-ttu-id="a1861-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a1861-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
