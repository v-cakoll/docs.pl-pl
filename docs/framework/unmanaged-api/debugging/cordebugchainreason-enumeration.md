---
title: "CorDebugChainReason — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1951983c9d167862169bd6178dc65693d724dc0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="5d279-102">CorDebugChainReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5d279-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="5d279-103">Wskazuje powód lub powody rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="5d279-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d279-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d279-104">Syntax</span></span>  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="5d279-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d279-105">Members</span></span>  
  
|<span data-ttu-id="5d279-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5d279-106">Member</span></span>|<span data-ttu-id="5d279-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5d279-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="5d279-108">Żaden łańcuch wywołań została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="5d279-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="5d279-109">Łańcuch został zainicjowany przez Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5d279-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="5d279-110">Łańcuch zostało zainicjowane przez filtru wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5d279-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="5d279-111">Łańcuch zostało zainicjowane przez kod, który wymusza zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d279-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="5d279-112">Łańcuch została zainicjowana przy użyciu zasad kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5d279-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="5d279-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="5d279-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="5d279-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="5d279-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="5d279-115">Łańcuch została zainicjowana przy rozpoczęciu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="5d279-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="5d279-116">Łańcuch zostało zainicjowane przez wejścia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5d279-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="5d279-117">Łańcuch zostało zainicjowane przez wejścia kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5d279-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="5d279-118">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="5d279-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="5d279-119">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="5d279-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="5d279-120">Łańcuch zostało zainicjowane przez Obliczanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d279-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d279-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d279-121">Remarks</span></span>  
 <span data-ttu-id="5d279-122">Użyj [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metodę, aby ustalić przyczyny rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="5d279-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d279-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d279-123">Requirements</span></span>  
 <span data-ttu-id="5d279-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d279-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d279-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d279-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d279-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d279-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d279-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d279-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d279-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d279-128">See Also</span></span>  
 [<span data-ttu-id="5d279-129">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5d279-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
