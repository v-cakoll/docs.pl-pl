---
title: Wyliczenie CorDebugDebugEventKind
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
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90cd2b8d02cb1d16e4932ffdcc3c9b02dc71541a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="10872-102">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="10872-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="10872-103">Wskazuje typ zdarzenia, których dane są dekodowane przez [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="10872-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10872-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10872-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="10872-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="10872-105">Members</span></span>  
  
|<span data-ttu-id="10872-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="10872-106">Member</span></span>|<span data-ttu-id="10872-107">Opis</span><span class="sxs-lookup"><span data-stu-id="10872-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="10872-108">Zdarzenie ładowania typu modułu.</span><span class="sxs-lookup"><span data-stu-id="10872-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="10872-109">To zdarzenie zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="10872-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="10872-110">Wyjątkach pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="10872-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="10872-111">Wyjątek pierwszej szansy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="10872-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="10872-112">Wystąpił wyjątek, dla którego `catch` Obsługa istnieje.</span><span class="sxs-lookup"><span data-stu-id="10872-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="10872-113">Wystąpił nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="10872-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10872-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10872-114">Remarks</span></span>  
 <span data-ttu-id="10872-115">Członek `CorDebugDebugEventKind` wyliczenie jest zwracany przez wywołanie metody [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="10872-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10872-116">To wyliczenie jest przeznaczona do użycia w platformę .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="10872-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10872-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10872-117">Requirements</span></span>  
 <span data-ttu-id="10872-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10872-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10872-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10872-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10872-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10872-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10872-121">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10872-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10872-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10872-122">See Also</span></span>  
 [<span data-ttu-id="10872-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="10872-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
