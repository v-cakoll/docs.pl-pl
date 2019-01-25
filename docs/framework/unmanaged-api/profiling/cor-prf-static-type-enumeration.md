---
title: COR_PRF_STATIC_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34a2ca5b505c504115af47402c3d92a05ec0676f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737640"
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="72065-102">COR_PRF_STATIC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="72065-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="72065-103">Wskazuje, czy pole jest statyczna, a jeśli tak, statycznej jakości, która odnosi się do pola.</span><span class="sxs-lookup"><span data-stu-id="72065-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="72065-104">Te wartości można łączyć, używając operacja bitowa lub w celu wskazania, że pole ma wiele różnych klas statycznych.</span><span class="sxs-lookup"><span data-stu-id="72065-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72065-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="72065-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="72065-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="72065-106">Members</span></span>  
  
|<span data-ttu-id="72065-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="72065-107">Member</span></span>|<span data-ttu-id="72065-108">Opis</span><span class="sxs-lookup"><span data-stu-id="72065-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="72065-109">Pole nie jest statyczne.</span><span class="sxs-lookup"><span data-stu-id="72065-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="72065-110">Pole nie jest statyczna domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72065-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="72065-111">Pole nie jest statyczna wątku.</span><span class="sxs-lookup"><span data-stu-id="72065-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="72065-112">Pole nie jest statyczna kontekstu.</span><span class="sxs-lookup"><span data-stu-id="72065-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="72065-113">To pole jest względnych adresów wirtualnych (RVA) — statyczne.</span><span class="sxs-lookup"><span data-stu-id="72065-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72065-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72065-114">Requirements</span></span>  
 <span data-ttu-id="72065-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72065-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72065-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72065-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72065-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72065-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72065-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72065-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72065-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72065-119">See also</span></span>
- [<span data-ttu-id="72065-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="72065-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
