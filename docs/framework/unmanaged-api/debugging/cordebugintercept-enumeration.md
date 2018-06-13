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
ms.openlocfilehash: 3ee2272a43d9f71cd49754a7f4233868b8bb9134
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406595"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="41bee-102">CorDebugIntercept — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="41bee-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="41bee-103">Wskazuje typy kodu, który może zostać przechwycony (tj. przeprowadził do).</span><span class="sxs-lookup"><span data-stu-id="41bee-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41bee-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="41bee-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41bee-105">Members</span></span>  
  
|<span data-ttu-id="41bee-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="41bee-106">Member</span></span>|<span data-ttu-id="41bee-107">Opis</span><span class="sxs-lookup"><span data-stu-id="41bee-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="41bee-108">Żaden kod nie może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="41bee-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="41bee-109">Konstruktor może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="41bee-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="41bee-110">Może zostać przechwycona filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="41bee-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="41bee-111">Kod, który wymusza zabezpieczeń mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="41bee-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="41bee-112">Może zostać przechwycona zasad kontekstu.</span><span class="sxs-lookup"><span data-stu-id="41bee-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="41bee-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="41bee-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="41bee-114">Cały kod może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="41bee-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41bee-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41bee-115">Remarks</span></span>  
 <span data-ttu-id="41bee-116">Użyj [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metody, aby określić typy kodu, który może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="41bee-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41bee-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41bee-117">Requirements</span></span>  
 <span data-ttu-id="41bee-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41bee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41bee-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41bee-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41bee-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41bee-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41bee-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41bee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bee-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41bee-122">See Also</span></span>  
 [<span data-ttu-id="41bee-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="41bee-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
