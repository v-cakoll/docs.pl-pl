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
ms.openlocfilehash: 894f74f12de7ed0754dcca34eacb815efc33c766
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752575"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="5a517-102">LogSwitchCallReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5a517-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="5a517-103">Określa operację, która została wykonana w przełączniku debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a517-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a517-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a517-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="5a517-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5a517-105">Members</span></span>  
  
|<span data-ttu-id="5a517-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5a517-106">Member</span></span>|<span data-ttu-id="5a517-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5a517-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="5a517-108">Przełącznik debugowanie śledzenia został utworzony.</span><span class="sxs-lookup"><span data-stu-id="5a517-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="5a517-109">Przełącznik debugowanie śledzenia został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="5a517-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="5a517-110">Usunięto przełącznik debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5a517-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a517-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a517-111">Requirements</span></span>  
 <span data-ttu-id="5a517-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a517-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a517-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a517-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a517-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a517-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a517-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a517-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a517-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a517-116">See also</span></span>

- [<span data-ttu-id="5a517-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5a517-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
