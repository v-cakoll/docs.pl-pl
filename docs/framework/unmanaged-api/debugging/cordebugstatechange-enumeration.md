---
title: Wyliczenie CorDebugStateChange
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStateChange
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: caf49621342be0ff85ac3cb56b95bb87f524c3be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="bf3a7-102">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="bf3a7-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="bf3a7-103">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="bf3a7-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf3a7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf3a7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="bf3a7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bf3a7-105">Members</span></span>  
  
|<span data-ttu-id="bf3a7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bf3a7-106">Member</span></span>|<span data-ttu-id="bf3a7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf3a7-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="bf3a7-108">Proces osiągnięto nowy stan pamięci przez wykonanie do przodu.</span><span class="sxs-lookup"><span data-stu-id="bf3a7-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="bf3a7-109">Pamięć procesu może być arbitralnie inny niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bf3a7-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf3a7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf3a7-110">Remarks</span></span>  
 <span data-ttu-id="bf3a7-111">Członek `CorDebugStateChange` wyliczenie jest podana jako wartość argumentu, gdy debuger wywołuje [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) — metoda</span><span class="sxs-lookup"><span data-stu-id="bf3a7-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf3a7-112">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="bf3a7-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf3a7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf3a7-113">Requirements</span></span>  
 <span data-ttu-id="bf3a7-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf3a7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf3a7-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf3a7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf3a7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf3a7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf3a7-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf3a7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf3a7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf3a7-118">See Also</span></span>  
 [<span data-ttu-id="bf3a7-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="bf3a7-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="bf3a7-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bf3a7-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
