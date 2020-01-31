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
ms.openlocfilehash: 977b1608539a302c6a27a1b54cfb2ad687025fe6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789407"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="4b3ab-102">CorDebugExceptionCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4b3ab-102">CorDebugExceptionCallbackType Enumeration</span></span>
<span data-ttu-id="4b3ab-103">Wskazuje typ wywołania zwrotnego, które jest wykonywane z [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4b3ab-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b3ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b3ab-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="4b3ab-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4b3ab-105">Members</span></span>  
  
|<span data-ttu-id="4b3ab-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4b3ab-106">Member</span></span>|<span data-ttu-id="4b3ab-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4b3ab-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="4b3ab-108">Zgłoszono wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4b3ab-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="4b3ab-109">Proces windup wyjątku wprowadził kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4b3ab-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="4b3ab-110">Proces windup wyjątku znalazł blok `catch` w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4b3ab-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="4b3ab-111">Wyjątek nie został obsłużony.</span><span class="sxs-lookup"><span data-stu-id="4b3ab-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4b3ab-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b3ab-112">Requirements</span></span>  
 <span data-ttu-id="4b3ab-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b3ab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b3ab-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4b3ab-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b3ab-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4b3ab-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b3ab-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b3ab-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3ab-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b3ab-117">See also</span></span>

- [<span data-ttu-id="4b3ab-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4b3ab-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
