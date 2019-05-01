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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786376"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="d0615-102">CorDebugExceptionUnwindCallbackType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d0615-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="d0615-103">Określa zdarzenie, które jest jest sygnalizowane przez wywołania zwrotnego w fazie unwind.</span><span class="sxs-lookup"><span data-stu-id="d0615-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0615-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0615-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="d0615-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0615-105">Members</span></span>  
  
|<span data-ttu-id="d0615-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d0615-106">Member</span></span>|<span data-ttu-id="d0615-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d0615-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="d0615-108">Początek procesu odwijania.</span><span class="sxs-lookup"><span data-stu-id="d0615-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="d0615-109">Wyjątek został przechwycony.</span><span class="sxs-lookup"><span data-stu-id="d0615-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0615-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0615-110">Requirements</span></span>  
 <span data-ttu-id="d0615-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0615-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0615-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0615-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0615-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0615-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0615-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0615-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0615-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d0615-115">See also</span></span>

- [<span data-ttu-id="d0615-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d0615-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
