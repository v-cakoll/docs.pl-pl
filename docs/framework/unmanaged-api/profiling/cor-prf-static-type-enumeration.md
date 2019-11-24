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
ms.openlocfilehash: 40efe81f72a2043503bf521e3e47dad1a7f4530c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448453"
---
# <a name="cor_prf_static_type-enumeration"></a><span data-ttu-id="a5a94-102">COR_PRF_STATIC_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a5a94-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="a5a94-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span><span class="sxs-lookup"><span data-stu-id="a5a94-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="a5a94-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span><span class="sxs-lookup"><span data-stu-id="a5a94-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5a94-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5a94-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="a5a94-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a5a94-106">Members</span></span>  
  
|<span data-ttu-id="a5a94-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a5a94-107">Member</span></span>|<span data-ttu-id="a5a94-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a5a94-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="a5a94-109">The field is not static.</span><span class="sxs-lookup"><span data-stu-id="a5a94-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="a5a94-110">The field is application domain-static.</span><span class="sxs-lookup"><span data-stu-id="a5a94-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="a5a94-111">The field is thread-static.</span><span class="sxs-lookup"><span data-stu-id="a5a94-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="a5a94-112">The field is context-static.</span><span class="sxs-lookup"><span data-stu-id="a5a94-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="a5a94-113">The field is relative virtual address (RVA)-static.</span><span class="sxs-lookup"><span data-stu-id="a5a94-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5a94-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5a94-114">Requirements</span></span>  
 <span data-ttu-id="a5a94-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5a94-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5a94-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5a94-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5a94-117">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5a94-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5a94-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5a94-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a94-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5a94-119">See also</span></span>

- [<span data-ttu-id="a5a94-120">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a5a94-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
