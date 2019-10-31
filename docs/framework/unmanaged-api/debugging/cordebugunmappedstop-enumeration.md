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
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132745"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="6fbcb-102">CorDebugUnmappedStop — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6fbcb-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="6fbcb-103">Określa typ niezamapowanego kodu, który może wyzwolić zatrzymanie w wykonaniu kodu przez stepper.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fbcb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fbcb-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="6fbcb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6fbcb-105">Members</span></span>  
  
|<span data-ttu-id="6fbcb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6fbcb-106">Member</span></span>|<span data-ttu-id="6fbcb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6fbcb-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="6fbcb-108">Nie należy Zatrzymywać w żadnym typie niezamapowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="6fbcb-109">Zatrzymaj w kodzie prologu.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="6fbcb-110">Zatrzymywanie w kodzie epilogu.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="6fbcb-111">Zatrzymaj w kodzie, który nie zawiera informacji dotyczących mapowania.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="6fbcb-112">Zatrzymaj w niemapowanym kodzie, który nie mieści się w niezgodnej kategorii Prolog, epilogu, Brak-mapowania-informacje lub niezarządzana.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="6fbcb-113">Zatrzymaj w kodzie niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-113">Stop in unmanaged code.</span></span> <span data-ttu-id="6fbcb-114">Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="6fbcb-115">Zatrzymaj wszystkie typy niezamapowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fbcb-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fbcb-116">Remarks</span></span>  
 <span data-ttu-id="6fbcb-117">Użyj metody [ICorDebugStepper:: SetUnmappedStopMask —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) , aby ustawić flagi określające niezamapowany kod, w którym zostanie zatrzymany stepper.</span><span class="sxs-lookup"><span data-stu-id="6fbcb-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fbcb-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fbcb-118">Requirements</span></span>  
 <span data-ttu-id="6fbcb-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fbcb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fbcb-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fbcb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fbcb-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fbcb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fbcb-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fbcb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbcb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fbcb-123">See also</span></span>

- [<span data-ttu-id="6fbcb-124">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6fbcb-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
