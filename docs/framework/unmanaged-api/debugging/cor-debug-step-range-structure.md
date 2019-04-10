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
ms.openlocfilehash: 57d7c3256d7b52a4e55dbb5bc420b0438983d2f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219684"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="9ef20-102">COR_DEBUG_STEP_RANGE — Struktura</span><span class="sxs-lookup"><span data-stu-id="9ef20-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="9ef20-103">Zawiera informacje przesunięcia w zakresie kodu.</span><span class="sxs-lookup"><span data-stu-id="9ef20-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="9ef20-104">Ta struktura jest używany przez [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9ef20-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef20-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ef20-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="9ef20-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9ef20-106">Members</span></span>  
  
|<span data-ttu-id="9ef20-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9ef20-107">Member</span></span>|<span data-ttu-id="9ef20-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9ef20-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="9ef20-109">Przesunięcie początku zakresu.</span><span class="sxs-lookup"><span data-stu-id="9ef20-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="9ef20-110">Przesunięcie koniec zakresu.</span><span class="sxs-lookup"><span data-stu-id="9ef20-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ef20-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ef20-111">Requirements</span></span>  
 <span data-ttu-id="9ef20-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ef20-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef20-113">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="9ef20-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="9ef20-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef20-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9ef20-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9ef20-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ef20-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ef20-116">See also</span></span>

- [<span data-ttu-id="9ef20-117">StepRange, metoda</span><span class="sxs-lookup"><span data-stu-id="9ef20-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="9ef20-118">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="9ef20-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="9ef20-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9ef20-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
