---
title: Wyliczenie CorDebugDebugEventKind
ms.date: 03/30/2017
api_name:
- CorDebugDebugEventKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type:
- apiref
ms.openlocfilehash: de4ac1f39ea9cfb4b616bd4e2c85e5de530dbb0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132229"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="d9f58-102">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="d9f58-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="d9f58-103">Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9f58-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9f58-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9f58-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="d9f58-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d9f58-105">Members</span></span>  
  
|<span data-ttu-id="d9f58-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d9f58-106">Member</span></span>|<span data-ttu-id="d9f58-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d9f58-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="d9f58-108">Zdarzenie ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="d9f58-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="d9f58-109">Zdarzenie Unload modułu.</span><span class="sxs-lookup"><span data-stu-id="d9f58-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="d9f58-110">Wyjątek pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="d9f58-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="d9f58-111">Wyjątek użytkownika pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="d9f58-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="d9f58-112">Wyjątek, dla którego istnieje procedura obsługi `catch`.</span><span class="sxs-lookup"><span data-stu-id="d9f58-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="d9f58-113">Nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d9f58-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9f58-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9f58-114">Remarks</span></span>  
 <span data-ttu-id="d9f58-115">Element członkowski wyliczenia `CorDebugDebugEventKind` jest zwracany przez wywołanie metody [ICorDebugDebugEvent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d9f58-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9f58-116">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d9f58-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9f58-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9f58-117">Requirements</span></span>  
 <span data-ttu-id="d9f58-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9f58-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9f58-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9f58-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9f58-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d9f58-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9f58-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9f58-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9f58-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9f58-122">See also</span></span>

- [<span data-ttu-id="d9f58-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d9f58-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
