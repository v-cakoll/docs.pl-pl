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
ms.openlocfilehash: c1cea8adcd12ecb3078e4469e6b018ed49064e0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175932"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="f555c-102">CorDebugUnmappedStop — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f555c-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="f555c-103">Określa typ niezamapowane kod, który możesz wyzwolić stepper zatrzymania wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="f555c-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f555c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f555c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f555c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f555c-105">Members</span></span>  
  
|<span data-ttu-id="f555c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f555c-106">Member</span></span>|<span data-ttu-id="f555c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f555c-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="f555c-108">Nie zostanie zatrzymana w dowolnego typu niezamapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="f555c-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="f555c-109">Zatrzymaj w kodzie prologu.</span><span class="sxs-lookup"><span data-stu-id="f555c-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="f555c-110">Zatrzymaj w kod epilogu.</span><span class="sxs-lookup"><span data-stu-id="f555c-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="f555c-111">Zatrzymaj w kodzie, który nie ma mapowania informacji.</span><span class="sxs-lookup"><span data-stu-id="f555c-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="f555c-112">Zatrzymaj w niezamapowane kod, który nie mieści się w prologu, epilogu, nie informacji o mapowaniu lub niezarządzanego kategorii.</span><span class="sxs-lookup"><span data-stu-id="f555c-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="f555c-113">Zatrzymaj w niezarządzanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f555c-113">Stop in unmanaged code.</span></span> <span data-ttu-id="f555c-114">Ta wartość jest prawidłowa tylko w przypadku debugowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="f555c-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="f555c-115">Zatrzymaj we wszystkich typach niezamapowane kodu.</span><span class="sxs-lookup"><span data-stu-id="f555c-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f555c-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f555c-116">Remarks</span></span>  
 <span data-ttu-id="f555c-117">Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metodę, aby ustawić flagi określające niezamapowane kodu, w którym stepper zostanie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="f555c-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f555c-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f555c-118">Requirements</span></span>  
 <span data-ttu-id="f555c-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f555c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f555c-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f555c-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f555c-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f555c-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f555c-122">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f555c-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f555c-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f555c-123">See also</span></span>

- [<span data-ttu-id="f555c-124">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f555c-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
