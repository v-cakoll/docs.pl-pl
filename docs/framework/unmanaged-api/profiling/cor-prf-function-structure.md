---
title: COR_PRF_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION
helpviewer_keywords:
- COR_PRF_FUNCTION structure [.NET Framework profiling]
ms.assetid: 8bb5acf5-cf4b-4ccb-93f1-46db1f3f8bf3
topic_type:
- apiref
ms.openlocfilehash: 856e01c7934709a17556aa53851204bf6a917de8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500939"
---
# <a name="cor_prf_function-structure"></a><span data-ttu-id="ecaf2-102">COR_PRF_FUNCTION — Struktura</span><span class="sxs-lookup"><span data-stu-id="ecaf2-102">COR_PRF_FUNCTION Structure</span></span>
<span data-ttu-id="ecaf2-103">Zapewnia unikatową reprezentację funkcji przez połączenie jej identyfikatora z IDENTYFIKATORem jego ponownie skompilowanej wersji.</span><span class="sxs-lookup"><span data-stu-id="ecaf2-103">Provides a unique representation of a function by combining its ID with the ID of its recompiled version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecaf2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecaf2-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_FUNCTION {    FunctionID functionId;    ReJITID    reJitId;} COR_PRF_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="ecaf2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ecaf2-105">Members</span></span>  
  
|<span data-ttu-id="ecaf2-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ecaf2-106">Member</span></span>|<span data-ttu-id="ecaf2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ecaf2-107">Description</span></span>|  
|------------|-----------------|  
|`functionId`|<span data-ttu-id="ecaf2-108">Identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="ecaf2-108">The ID of the function.</span></span>|  
|`reJitId`|<span data-ttu-id="ecaf2-109">Identyfikator ponownie skompilowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="ecaf2-109">The ID of the recompiled function.</span></span> <span data-ttu-id="ecaf2-110">Wartość 0 (zero) reprezentuje oryginalną wersję funkcji.</span><span class="sxs-lookup"><span data-stu-id="ecaf2-110">A value of 0 (zero) represents the original version of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecaf2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecaf2-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecaf2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecaf2-112">Requirements</span></span>  
 <span data-ttu-id="ecaf2-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecaf2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecaf2-114">**Nagłówek:** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="ecaf2-114">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ecaf2-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecaf2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecaf2-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecaf2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaf2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecaf2-117">See also</span></span>

- [<span data-ttu-id="ecaf2-118">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="ecaf2-118">Profiling Structures</span></span>](profiling-structures.md)
