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
ms.openlocfilehash: b7db7c9e17d87b91e09d5d010d40431cba5385df
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795992"
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="b8142-102">Wyliczenie CorDebugDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="b8142-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="b8142-103">Wskazuje typ zdarzenia, którego informacje są dekodowane przez metodę [DecodeEvent](icordebugprocess6-decodeevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b8142-103">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8142-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8142-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b8142-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b8142-105">Members</span></span>  
  
|<span data-ttu-id="b8142-106">Członek</span><span class="sxs-lookup"><span data-stu-id="b8142-106">Member</span></span>|<span data-ttu-id="b8142-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b8142-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="b8142-108">Zdarzenie ładowania modułu.</span><span class="sxs-lookup"><span data-stu-id="b8142-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="b8142-109">Zdarzenie Unload modułu.</span><span class="sxs-lookup"><span data-stu-id="b8142-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="b8142-110">Wyjątek pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="b8142-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="b8142-111">Wyjątek użytkownika pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="b8142-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="b8142-112">Wyjątek, dla którego istnieje `catch` program obsługi.</span><span class="sxs-lookup"><span data-stu-id="b8142-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="b8142-113">Nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b8142-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8142-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8142-114">Remarks</span></span>  
 <span data-ttu-id="b8142-115">Element członkowski `CorDebugDebugEventKind` wyliczenia jest zwracany przez wywołanie metody [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b8142-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8142-116">To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8142-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8142-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8142-117">Requirements</span></span>  
 <span data-ttu-id="b8142-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8142-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8142-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8142-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8142-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b8142-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8142-121">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8142-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8142-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8142-122">See also</span></span>

- [<span data-ttu-id="b8142-123">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b8142-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
