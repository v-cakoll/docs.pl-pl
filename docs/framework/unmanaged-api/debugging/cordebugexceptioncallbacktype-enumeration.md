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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91b09be04499396a2229962fd592f29cb8bc8d04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609041"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="8cea7-102">CorDebugExceptionCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8cea7-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="8cea7-103">Wskazuje typ wywołanie zwrotne, które zostało wprowadzone przy użyciu [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8cea7-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cea7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cea7-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="8cea7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8cea7-105">Members</span></span>  
  
|<span data-ttu-id="8cea7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8cea7-106">Member</span></span>|<span data-ttu-id="8cea7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8cea7-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="8cea7-108">Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8cea7-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="8cea7-109">Proces windup wyjątek wprowadzić kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8cea7-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="8cea7-110">Wyjątek procesu windup `catch` blokowania w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8cea7-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="8cea7-111">Wyjątek nie został obsłużony.</span><span class="sxs-lookup"><span data-stu-id="8cea7-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8cea7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cea7-112">Requirements</span></span>  
 <span data-ttu-id="8cea7-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cea7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cea7-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cea7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cea7-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cea7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cea7-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cea7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cea7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cea7-117">See also</span></span>

- [<span data-ttu-id="8cea7-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8cea7-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
