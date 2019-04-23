---
title: CorDebugExceptionUnwindCallbackType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408e72eeaa1dac83c45488d186425f30c6043280
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155626"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="3a50f-102">CorDebugExceptionUnwindCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3a50f-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="3a50f-103">Określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="3a50f-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a50f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a50f-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="3a50f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3a50f-105">Members</span></span>  
  
|<span data-ttu-id="3a50f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3a50f-106">Member</span></span>|<span data-ttu-id="3a50f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3a50f-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="3a50f-108">Początek procesu odwijania.</span><span class="sxs-lookup"><span data-stu-id="3a50f-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="3a50f-109">Wyjątek został przechwycony.</span><span class="sxs-lookup"><span data-stu-id="3a50f-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a50f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a50f-110">Requirements</span></span>  
 <span data-ttu-id="3a50f-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a50f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a50f-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a50f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a50f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a50f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a50f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a50f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a50f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a50f-115">See also</span></span>

- [<span data-ttu-id="3a50f-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3a50f-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
