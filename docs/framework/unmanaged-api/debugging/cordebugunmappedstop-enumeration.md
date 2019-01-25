---
title: CorDebugUnmappedStop — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f22c045be9af71644415ae3b6b5e64d3e399dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495438"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="21785-102">CorDebugUnmappedStop — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="21785-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="21785-103">Określa typ niezamapowane kod, który możesz wyzwolić stepper zatrzymania wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="21785-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21785-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21785-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="21785-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="21785-105">Members</span></span>  
  
|<span data-ttu-id="21785-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="21785-106">Member</span></span>|<span data-ttu-id="21785-107">Opis</span><span class="sxs-lookup"><span data-stu-id="21785-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="21785-108">Nie zostanie zatrzymana w dowolnego typu niezamapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="21785-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="21785-109">Zatrzymaj w kodzie prologu.</span><span class="sxs-lookup"><span data-stu-id="21785-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="21785-110">Zatrzymaj w kod epilogu.</span><span class="sxs-lookup"><span data-stu-id="21785-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="21785-111">Zatrzymaj w kodzie, który nie ma mapowania informacji.</span><span class="sxs-lookup"><span data-stu-id="21785-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="21785-112">Zatrzymaj w niezamapowane kod, który nie mieści się w prologu, epilogu, nie informacji o mapowaniu lub niezarządzanego kategorii.</span><span class="sxs-lookup"><span data-stu-id="21785-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="21785-113">Zatrzymaj w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="21785-113">Stop in unmanaged code.</span></span> <span data-ttu-id="21785-114">Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="21785-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="21785-115">Zatrzymaj we wszystkich typach niezamapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="21785-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21785-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21785-116">Remarks</span></span>  
 <span data-ttu-id="21785-117">Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metodę, aby ustawić flagi określające niezamapowane kodu, w którym stepper zostanie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="21785-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21785-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21785-118">Requirements</span></span>  
 <span data-ttu-id="21785-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21785-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21785-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21785-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21785-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21785-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21785-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21785-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21785-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21785-123">See also</span></span>
- [<span data-ttu-id="21785-124">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="21785-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
