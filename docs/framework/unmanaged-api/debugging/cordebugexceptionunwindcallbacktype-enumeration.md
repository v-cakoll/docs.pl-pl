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
ms.openlocfilehash: 4d2be9960f8935b754791a8badd4ea98b5d54912
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795914"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="54486-102">CorDebugExceptionUnwindCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="54486-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="54486-103">Wskazuje zdarzenie, które jest sygnalizowane przez wywołanie zwrotne w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="54486-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54486-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54486-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="54486-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="54486-105">Members</span></span>  
  
|<span data-ttu-id="54486-106">Członek</span><span class="sxs-lookup"><span data-stu-id="54486-106">Member</span></span>|<span data-ttu-id="54486-107">Opis</span><span class="sxs-lookup"><span data-stu-id="54486-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="54486-108">Początek procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="54486-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="54486-109">Przechwycono wyjątek.</span><span class="sxs-lookup"><span data-stu-id="54486-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54486-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54486-110">Requirements</span></span>  
 <span data-ttu-id="54486-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54486-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54486-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="54486-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54486-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="54486-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54486-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54486-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54486-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54486-115">See also</span></span>

- [<span data-ttu-id="54486-116">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="54486-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
