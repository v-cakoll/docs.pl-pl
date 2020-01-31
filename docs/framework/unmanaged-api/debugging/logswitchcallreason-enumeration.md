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
ms.openlocfilehash: 29781666c106755f96f945325e3a8953bf93b211
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790344"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="28422-102">LogSwitchCallReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="28422-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="28422-103">Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28422-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28422-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28422-104">Syntax</span></span>  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="28422-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="28422-105">Members</span></span>  
  
|<span data-ttu-id="28422-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="28422-106">Member</span></span>|<span data-ttu-id="28422-107">Opis</span><span class="sxs-lookup"><span data-stu-id="28422-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="28422-108">Utworzono przełącznik debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28422-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="28422-109">Zmodyfikowano przełącznik debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28422-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="28422-110">Usunięto przełącznik debugowania/śledzenia.</span><span class="sxs-lookup"><span data-stu-id="28422-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28422-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28422-111">Requirements</span></span>  
 <span data-ttu-id="28422-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28422-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28422-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28422-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28422-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28422-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28422-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28422-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28422-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28422-116">See also</span></span>

- [<span data-ttu-id="28422-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="28422-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
