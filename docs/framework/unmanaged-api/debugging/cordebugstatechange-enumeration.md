---
title: Wyliczenie CorDebugStateChange
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513792"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="753c9-102">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="753c9-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="753c9-103">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="753c9-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="753c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="753c9-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="753c9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="753c9-105">Members</span></span>  
  
|<span data-ttu-id="753c9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="753c9-106">Member</span></span>|<span data-ttu-id="753c9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="753c9-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="753c9-108">Proces osiągnięto nowy stan pamięci za pomocą wykonywania do przodu.</span><span class="sxs-lookup"><span data-stu-id="753c9-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="753c9-109">Pamięć procesu może być dowolnie inny niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="753c9-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="753c9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="753c9-110">Remarks</span></span>  
 <span data-ttu-id="753c9-111">Członek `CorDebugStateChange` wyliczenia jest dostarczana jako argument, gdy wywołuje debugera [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) — metoda</span><span class="sxs-lookup"><span data-stu-id="753c9-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="753c9-112">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="753c9-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="753c9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="753c9-113">Requirements</span></span>  
 <span data-ttu-id="753c9-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="753c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="753c9-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="753c9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="753c9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="753c9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="753c9-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="753c9-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753c9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="753c9-118">See also</span></span>
- [<span data-ttu-id="753c9-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="753c9-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="753c9-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="753c9-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
