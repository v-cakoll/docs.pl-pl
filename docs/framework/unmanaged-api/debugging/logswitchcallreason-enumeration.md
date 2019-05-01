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
ms.openlocfilehash: 7eadb595eb62b4f1a9dcc888225cbb7454119c7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986547"
---
# <a name="logswitchcallreason-enumeration"></a><span data-ttu-id="b9429-102">LogSwitchCallReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b9429-102">LogSwitchCallReason Enumeration</span></span>
<span data-ttu-id="b9429-103">Określa operację, która została wykonana w przełączniku debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b9429-103">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9429-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9429-104">Syntax</span></span>  
  
```  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a><span data-ttu-id="b9429-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b9429-105">Members</span></span>  
  
|<span data-ttu-id="b9429-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b9429-106">Member</span></span>|<span data-ttu-id="b9429-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b9429-107">Description</span></span>|  
|------------|-----------------|  
|`SWITCH_CREATE`|<span data-ttu-id="b9429-108">Przełącznik debugowanie śledzenia został utworzony.</span><span class="sxs-lookup"><span data-stu-id="b9429-108">A debugging/tracing switch was created.</span></span>|  
|`SWITCH_MODIFY`|<span data-ttu-id="b9429-109">Przełącznik debugowanie śledzenia został zmodyfikowany.</span><span class="sxs-lookup"><span data-stu-id="b9429-109">A debugging/tracing switch was modified.</span></span>|  
|`SWITCH_DELETE`|<span data-ttu-id="b9429-110">Usunięto przełącznik debugowanie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b9429-110">A debugging/tracing switch was deleted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9429-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9429-111">Requirements</span></span>  
 <span data-ttu-id="b9429-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9429-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9429-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9429-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9429-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9429-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9429-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9429-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9429-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9429-116">See also</span></span>

- [<span data-ttu-id="b9429-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b9429-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
