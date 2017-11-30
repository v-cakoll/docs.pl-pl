---
title: "CorDebugBlockingObject — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingObject Structure
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingObject
helpviewer_keywords: CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c47735565c960c2600f7274d0d59d5a6ec6c178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="bbc10-102">CorDebugBlockingObject — Struktura</span><span class="sxs-lookup"><span data-stu-id="bbc10-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="bbc10-103">Definiuje obiekt, który blokuje wątku i powód, że wątek jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="bbc10-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbc10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbc10-104">Syntax</span></span>  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="bbc10-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bbc10-105">Members</span></span>  
  
|<span data-ttu-id="bbc10-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bbc10-106">Member</span></span>|<span data-ttu-id="bbc10-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bbc10-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="bbc10-108">Obiekt, w którym wątek jest zablokowana.</span><span class="sxs-lookup"><span data-stu-id="bbc10-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="bbc10-109">Ten obiekt jest prawidłowy tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="bbc10-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="bbc10-110">Jeśli na tym samym obiekcie, w ramach tego samego stanu zsynchronizowanych blokują dwoma wątkami, może spodziewać się [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody zwracają taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="bbc10-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="bbc10-111">Jednak interfejsy może lub nie może być wskaźnika równoważne.</span><span class="sxs-lookup"><span data-stu-id="bbc10-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="bbc10-112">Wyrażony w milisekundach czas, przed wykonaniem operacji blokowania będzie limitu czasu lub wartość INFINITE, co oznacza, że będzie on nie upłynął limit czasu. Wartość limitu czasu określa całkowity czas blokowania operacji, nie jest nadal pozostały czas.</span><span class="sxs-lookup"><span data-stu-id="bbc10-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="bbc10-113">Powód, że wątek jest zablokowany na tym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="bbc10-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbc10-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbc10-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbc10-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbc10-115">Requirements</span></span>  
 <span data-ttu-id="bbc10-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbc10-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbc10-117">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="bbc10-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="bbc10-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbc10-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbc10-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbc10-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc10-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbc10-120">See Also</span></span>  
 [<span data-ttu-id="bbc10-121">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="bbc10-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="bbc10-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bbc10-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
