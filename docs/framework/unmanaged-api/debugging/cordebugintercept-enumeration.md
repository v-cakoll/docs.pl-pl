---
title: CorDebugIntercept — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651704"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="a790a-102">CorDebugIntercept — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a790a-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="a790a-103">Określa typy kodu, która może zostać przechwycona (który jest zmieniana do).</span><span class="sxs-lookup"><span data-stu-id="a790a-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a790a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a790a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="a790a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a790a-105">Members</span></span>  
  
|<span data-ttu-id="a790a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a790a-106">Member</span></span>|<span data-ttu-id="a790a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a790a-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="a790a-108">Brak kodu mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a790a-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="a790a-109">Konstruktor mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a790a-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="a790a-110">Mogą zostać przechwycone filtra wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a790a-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="a790a-111">Kod, który wymusza zabezpieczeń mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a790a-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="a790a-112">Zasady kontekstu może zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a790a-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="a790a-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a790a-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="a790a-114">Cały kod może zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="a790a-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a790a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a790a-115">Remarks</span></span>  
 <span data-ttu-id="a790a-116">Użyj [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metodę, aby określić typy kodu, która może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="a790a-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a790a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a790a-117">Requirements</span></span>  
 <span data-ttu-id="a790a-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a790a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a790a-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a790a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a790a-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a790a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a790a-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a790a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a790a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a790a-122">See also</span></span>

- [<span data-ttu-id="a790a-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a790a-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
