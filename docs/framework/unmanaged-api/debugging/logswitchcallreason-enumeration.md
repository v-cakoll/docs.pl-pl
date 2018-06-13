---
title: LogSwitchCallReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fe5710f1be0bfa4e651668e2469c3551ad79261
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423835"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="a948c-102">LogSwitchCallReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a948c-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="a948c-103">Wskazuje działanie zostało wykonane na przełączniku debugowania śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a948c-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a948c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a948c-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="a948c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a948c-105">Members</span></span>  
  
|<span data-ttu-id="a948c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a948c-106">Member</span></span>|<span data-ttu-id="a948c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a948c-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="a948c-108">Przełącznik debugowania śledzenia został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a948c-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="a948c-109">Przełącznik debugowania śledzenia został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="a948c-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="a948c-110">Przełącznik debugowania śledzenia został usunięty.</span><span class="sxs-lookup"><span data-stu-id="a948c-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a948c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a948c-111">Requirements</span></span>  
 <span data-ttu-id="a948c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a948c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a948c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a948c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a948c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a948c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a948c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a948c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a948c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a948c-116">See Also</span></span>  
 [<span data-ttu-id="a948c-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a948c-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
