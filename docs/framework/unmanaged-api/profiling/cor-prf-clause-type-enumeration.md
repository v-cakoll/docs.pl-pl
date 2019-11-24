---
title: COR_PRF_CLAUSE_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_CLAUSE_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CLAUSE_TYPE
helpviewer_keywords:
- COR_PRF_CLAUSE_TYPE enumeration [.NET Framework profiling]
ms.assetid: f64c325a-ed3a-4aaf-b847-a88edbc4fefc
topic_type:
- apiref
ms.openlocfilehash: 94230cbad95ff0a5d4234c27aa5d1d56ac5be9bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428399"
---
# <a name="cor_prf_clause_type-enumeration"></a><span data-ttu-id="ca24d-102">COR_PRF_CLAUSE_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ca24d-102">COR_PRF_CLAUSE_TYPE Enumeration</span></span>
<span data-ttu-id="ca24d-103">Indicates the type of exception clause that the code has just entered or left.</span><span class="sxs-lookup"><span data-stu-id="ca24d-103">Indicates the type of exception clause that the code has just entered or left.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca24d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca24d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CLAUSE_NONE = 0,  
    COR_PRF_CLAUSE_FILTER = 1,  
    COR_PRF_CLAUSE_CATCH = 2,  
    COR_PRF_CLAUSE_FINALLY = 3,  
} COR_PRF_CLAUSE_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ca24d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ca24d-105">Members</span></span>  
  
|<span data-ttu-id="ca24d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ca24d-106">Member</span></span>|<span data-ttu-id="ca24d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ca24d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CLAUSE_NONE`|<span data-ttu-id="ca24d-108">The exception clause is not valid.</span><span class="sxs-lookup"><span data-stu-id="ca24d-108">The exception clause is not valid.</span></span>|  
|`COR_PRF_CLAUSE_FILTER`|<span data-ttu-id="ca24d-109">The exception clause is a filter expression.</span><span class="sxs-lookup"><span data-stu-id="ca24d-109">The exception clause is a filter expression.</span></span>|  
|`COR_PRF_CLAUSE_CATCH`|<span data-ttu-id="ca24d-110">The exception clause is a `catch` statement.</span><span class="sxs-lookup"><span data-stu-id="ca24d-110">The exception clause is a `catch` statement.</span></span>|  
|`COR_PRF_CLAUSE_FINALLY`|<span data-ttu-id="ca24d-111">The exception clause is a `finally` statement.</span><span class="sxs-lookup"><span data-stu-id="ca24d-111">The exception clause is a `finally` statement.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca24d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca24d-112">Requirements</span></span>  
 <span data-ttu-id="ca24d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca24d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca24d-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca24d-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca24d-115">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca24d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca24d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca24d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca24d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca24d-117">See also</span></span>

- [<span data-ttu-id="ca24d-118">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ca24d-118">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
