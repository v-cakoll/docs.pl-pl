---
title: CorDebugExceptionCallbackType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: c927dcde99f5217ee7c160359385e0b953034380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132240"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="d14c8-102">CorDebugExceptionCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d14c8-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="d14c8-103">Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d14c8-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d14c8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="d14c8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d14c8-105">Members</span></span>  
  
|<span data-ttu-id="d14c8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d14c8-106">Member</span></span>|<span data-ttu-id="d14c8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d14c8-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="d14c8-108">Zgłoszono wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d14c8-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="d14c8-109">Proces windup wyjątku wprowadził kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d14c8-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="d14c8-110">Proces windup wyjątku znalazł blok `catch` w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d14c8-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="d14c8-111">Wyjątek nie został obsłużony.</span><span class="sxs-lookup"><span data-stu-id="d14c8-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d14c8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d14c8-112">Requirements</span></span>  
 <span data-ttu-id="d14c8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d14c8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d14c8-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d14c8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d14c8-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d14c8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d14c8-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d14c8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d14c8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d14c8-117">See also</span></span>

- [<span data-ttu-id="d14c8-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d14c8-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
