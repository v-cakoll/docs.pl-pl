---
title: "CorDebugUnmappedStop — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUnmappedStop
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUnmappedStop
helpviewer_keywords: CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e75c827533a921c4cab31b2e8b0996dffa532fe2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="2b6da-102">CorDebugUnmappedStop — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2b6da-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="2b6da-103">Określa typ Niemapowane kodu, które mogą wyzwalać zatrzymania wykonywania kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="2b6da-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b6da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b6da-104">Syntax</span></span>  
  
```  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="2b6da-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2b6da-105">Members</span></span>  
  
|<span data-ttu-id="2b6da-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2b6da-106">Member</span></span>|<span data-ttu-id="2b6da-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2b6da-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="2b6da-108">Nie zostanie zatrzymana w typu Niemapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="2b6da-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="2b6da-109">Zatrzymaj w prologu kodu.</span><span class="sxs-lookup"><span data-stu-id="2b6da-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="2b6da-110">Kod epilogu zatrzyma.</span><span class="sxs-lookup"><span data-stu-id="2b6da-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="2b6da-111">Zatrzymanie w kodzie, który nie ma mapowania informacji.</span><span class="sxs-lookup"><span data-stu-id="2b6da-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="2b6da-112">Zatrzymaj Niemapowane kodu, który nie mieści się w prologu, epilogu, nie informacje dotyczące mapowania lub niezarządzane kategorii.</span><span class="sxs-lookup"><span data-stu-id="2b6da-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="2b6da-113">Zatrzymaj za pomocą kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2b6da-113">Stop in unmanaged code.</span></span> <span data-ttu-id="2b6da-114">Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2b6da-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="2b6da-115">Zatrzymaj we wszystkich typach Niemapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="2b6da-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b6da-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b6da-116">Remarks</span></span>  
 <span data-ttu-id="2b6da-117">Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metody można ustawić flagi określające Niemapowane kodu, w którym stepper zostanie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="2b6da-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b6da-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b6da-118">Requirements</span></span>  
 <span data-ttu-id="2b6da-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b6da-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b6da-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b6da-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b6da-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b6da-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b6da-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b6da-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6da-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b6da-123">See Also</span></span>  
 [<span data-ttu-id="2b6da-124">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b6da-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
