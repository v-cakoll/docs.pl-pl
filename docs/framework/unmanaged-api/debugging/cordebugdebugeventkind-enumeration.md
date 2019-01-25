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
ms.openlocfilehash: a45929c3eef5e9127e89dd88346c6207f3f1bc65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559501"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="8b5b7-102">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="8b5b7-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="8b5b7-103">Określa typ zdarzenia, o których informacje jest dekodowana przy [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b5b7-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8b5b7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8b5b7-105">Members</span></span>  
  
|<span data-ttu-id="8b5b7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8b5b7-106">Member</span></span>|<span data-ttu-id="8b5b7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8b5b7-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="8b5b7-108">Moduł załadowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="8b5b7-109">To zdarzenie zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="8b5b7-110">Wyjątek pierwszego rzędu.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="8b5b7-111">Wyjątku pierwszej szansy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="8b5b7-112">Wyjątek, dla którego `catch` istnieje program obsługi.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="8b5b7-113">Nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b5b7-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b5b7-114">Remarks</span></span>  
 <span data-ttu-id="8b5b7-115">Członek `CorDebugDebugEventKind` wyliczenia jest zwracany przez wywołanie metody [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b5b7-116">To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.</span><span class="sxs-lookup"><span data-stu-id="8b5b7-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5b7-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b5b7-117">Requirements</span></span>  
 <span data-ttu-id="8b5b7-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5b7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5b7-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b5b7-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b5b7-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b5b7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b5b7-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5b7-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5b7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b5b7-122">See also</span></span>
- [<span data-ttu-id="8b5b7-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8b5b7-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
