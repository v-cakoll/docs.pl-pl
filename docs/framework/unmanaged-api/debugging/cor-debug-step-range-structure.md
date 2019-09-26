---
title: COR_DEBUG_STEP_RANGE — Struktura
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11d5e2eb5e2743fca4876ed09add79be3eba514f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274206"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="31606-102">COR_DEBUG_STEP_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="31606-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="31606-103">Zawiera informacje o przesunięciu dla zakresu kodu.</span><span class="sxs-lookup"><span data-stu-id="31606-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="31606-104">Ta struktura jest używana przez metodę [ICorDebugStepper:: StepRange —](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="31606-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31606-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="31606-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="31606-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="31606-106">Members</span></span>  
  
|<span data-ttu-id="31606-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="31606-107">Member</span></span>|<span data-ttu-id="31606-108">Opis</span><span class="sxs-lookup"><span data-stu-id="31606-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="31606-109">Przesunięcie początku zakresu.</span><span class="sxs-lookup"><span data-stu-id="31606-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="31606-110">Przesunięcie końca zakresu.</span><span class="sxs-lookup"><span data-stu-id="31606-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="31606-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31606-111">Requirements</span></span>  
 <span data-ttu-id="31606-112">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31606-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31606-113">**Nagłówki** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="31606-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="31606-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31606-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31606-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31606-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31606-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31606-116">See also</span></span>

- [<span data-ttu-id="31606-117">StepRange, metoda</span><span class="sxs-lookup"><span data-stu-id="31606-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="31606-118">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="31606-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="31606-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31606-119">Debugging</span></span>](index.md)
