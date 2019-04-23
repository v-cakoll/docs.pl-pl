---
title: CorDebugChainReason — Wyliczenie
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190447"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="07904-102">CorDebugChainReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="07904-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="07904-103">Wskazuje powód lub powody do rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="07904-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07904-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07904-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="07904-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="07904-105">Members</span></span>  
  
|<span data-ttu-id="07904-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="07904-106">Member</span></span>|<span data-ttu-id="07904-107">Opis</span><span class="sxs-lookup"><span data-stu-id="07904-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="07904-108">Łańcuch wywołań, nie został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="07904-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="07904-109">Ciąg został zainicjowany przez Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="07904-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="07904-110">Łańcuch zostało zainicjowane przez filtra wyjątku.</span><span class="sxs-lookup"><span data-stu-id="07904-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="07904-111">Łańcuch zostało zainicjowane przez kod, który wymusza stosowanie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="07904-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="07904-112">Łańcuch zostało zainicjowane przez zasadę kontekstu.</span><span class="sxs-lookup"><span data-stu-id="07904-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="07904-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="07904-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="07904-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="07904-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="07904-115">Łańcuch zostało zainicjowane przez rozpoczęciem wykonywaniem wątków.</span><span class="sxs-lookup"><span data-stu-id="07904-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="07904-116">Łańcuch zostało zainicjowane przez wejścia w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="07904-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="07904-117">Łańcuch zostało zainicjowane przez wejścia w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="07904-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="07904-118">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="07904-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="07904-119">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="07904-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="07904-120">Łańcuch zostało zainicjowane przez Obliczanie funkcji.</span><span class="sxs-lookup"><span data-stu-id="07904-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07904-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07904-121">Remarks</span></span>  
 <span data-ttu-id="07904-122">Użyj [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metodę, aby ustalić przyczyny do rozpoczęcia łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="07904-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07904-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07904-123">Requirements</span></span>  
 <span data-ttu-id="07904-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07904-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07904-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07904-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07904-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07904-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07904-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07904-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07904-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07904-128">See also</span></span>

- [<span data-ttu-id="07904-129">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="07904-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
