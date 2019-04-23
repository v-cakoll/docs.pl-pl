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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199937"
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="ce9c0-102">CorDebugIntercept — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ce9c0-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="ce9c0-103">Określa typy kodu, która może zostać przechwycona (który jest zmieniana do).</span><span class="sxs-lookup"><span data-stu-id="ce9c0-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce9c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce9c0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ce9c0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ce9c0-105">Members</span></span>  
  
|<span data-ttu-id="ce9c0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ce9c0-106">Member</span></span>|<span data-ttu-id="ce9c0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ce9c0-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="ce9c0-108">Brak kodu mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="ce9c0-109">Konstruktor mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="ce9c0-110">Mogą zostać przechwycone filtra wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="ce9c0-111">Kod, który wymusza zabezpieczeń mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="ce9c0-112">Zasady kontekstu może zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="ce9c0-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="ce9c0-114">Cały kod może zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce9c0-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce9c0-115">Remarks</span></span>  
 <span data-ttu-id="ce9c0-116">Użyj [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metodę, aby określić typy kodu, która może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="ce9c0-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce9c0-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce9c0-117">Requirements</span></span>  
 <span data-ttu-id="ce9c0-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce9c0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce9c0-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce9c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce9c0-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce9c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce9c0-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce9c0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9c0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce9c0-122">See also</span></span>

- [<span data-ttu-id="ce9c0-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ce9c0-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
