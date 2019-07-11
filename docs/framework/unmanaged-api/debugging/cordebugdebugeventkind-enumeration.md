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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be8d860f508644e68bf69892a63e145e7ffd5b90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740242"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="9e0d1-102">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="9e0d1-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="9e0d1-103">Określa typ zdarzenia, o których informacje jest dekodowana przy [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e0d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e0d1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9e0d1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9e0d1-105">Members</span></span>  
  
|<span data-ttu-id="9e0d1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9e0d1-106">Member</span></span>|<span data-ttu-id="9e0d1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9e0d1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="9e0d1-108">Moduł załadowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="9e0d1-109">To zdarzenie zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="9e0d1-110">Wyjątek pierwszego rzędu.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="9e0d1-111">Wyjątku pierwszej szansy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="9e0d1-112">Wyjątek, dla którego `catch` istnieje program obsługi.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="9e0d1-113">Nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e0d1-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e0d1-114">Remarks</span></span>  
 <span data-ttu-id="9e0d1-115">Członek `CorDebugDebugEventKind` wyliczenia jest zwracany przez wywołanie metody [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e0d1-116">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="9e0d1-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e0d1-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e0d1-117">Requirements</span></span>  
 <span data-ttu-id="9e0d1-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0d1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0d1-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e0d1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e0d1-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e0d1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e0d1-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0d1-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0d1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e0d1-122">See also</span></span>

- [<span data-ttu-id="9e0d1-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9e0d1-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
