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
ms.openlocfilehash: 7fe2fcf10b517f4eb7b1c7e87142afb386821246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404121"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="c0922-102">CorDebugExceptionUnwindCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c0922-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="c0922-103">Wskazuje sygnalizowane trwa przez wywołanie zwrotne w fazie unwind zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c0922-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0922-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0922-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="c0922-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c0922-105">Members</span></span>  
  
|<span data-ttu-id="c0922-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c0922-106">Member</span></span>|<span data-ttu-id="c0922-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c0922-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="c0922-108">Na początku procesu unwind.</span><span class="sxs-lookup"><span data-stu-id="c0922-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="c0922-109">Wyjątek został przechwycony.</span><span class="sxs-lookup"><span data-stu-id="c0922-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0922-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0922-110">Requirements</span></span>  
 <span data-ttu-id="c0922-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0922-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0922-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0922-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0922-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0922-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0922-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0922-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0922-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0922-115">See Also</span></span>  
 [<span data-ttu-id="c0922-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c0922-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
