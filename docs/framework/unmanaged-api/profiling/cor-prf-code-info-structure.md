---
title: COR_PRF_CODE_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 643c9d7104c374d9141a604083f3fdcd540156c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428390"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="d1d51-102">COR_PRF_CODE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="d1d51-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="d1d51-103">Represents one contiguous block of native code stored in memory.</span><span class="sxs-lookup"><span data-stu-id="d1d51-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1d51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d51-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="d1d51-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d1d51-105">Members</span></span>  
  
|<span data-ttu-id="d1d51-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d1d51-106">Member</span></span>|<span data-ttu-id="d1d51-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d1d51-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="d1d51-108">The starting address of the contiguous block of code.</span><span class="sxs-lookup"><span data-stu-id="d1d51-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="d1d51-109">The size of the block.</span><span class="sxs-lookup"><span data-stu-id="d1d51-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1d51-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1d51-110">Requirements</span></span>  
 <span data-ttu-id="d1d51-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1d51-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1d51-112">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d1d51-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d1d51-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1d51-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1d51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1d51-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d51-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1d51-115">See also</span></span>

- [<span data-ttu-id="d1d51-116">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="d1d51-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
