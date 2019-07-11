---
title: CorDebugBlockingObject — Struktura
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83dac3b9b2ac396cdef19695fcce0f7e20485a50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740393"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="06f0f-102">CorDebugBlockingObject — Struktura</span><span class="sxs-lookup"><span data-stu-id="06f0f-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="06f0f-103">Definiuje obiekt, który blokuje wątek i powód, że wątek jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="06f0f-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06f0f-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="06f0f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="06f0f-105">Members</span></span>  
  
|<span data-ttu-id="06f0f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="06f0f-106">Member</span></span>|<span data-ttu-id="06f0f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="06f0f-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="06f0f-108">Obiekt, na którym blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="06f0f-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="06f0f-109">Ten obiekt jest prawidłowy tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="06f0f-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="06f0f-110">Jeśli dwa wątki są przeszkodą w ten sam obiekt w ramach zsynchronizowane takiego samego stanu, mogą oczekiwać [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody zwracają taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="06f0f-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="06f0f-111">Jednak interfejsy mogą lub nie może być wskaźnik równoważne.</span><span class="sxs-lookup"><span data-stu-id="06f0f-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="06f0f-112">Liczba milisekund, przed wykonaniem operacji blokowania będzie limit czasu lub wartości NIESKOŃCZONE, co oznacza, że będą wykonywane następujące czynności nie przekraczają limit czasu. Wartość limitu czasu określa długość całkowity czas blokowania operacji, nie jest jeszcze pozostało czasu.</span><span class="sxs-lookup"><span data-stu-id="06f0f-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="06f0f-113">Powód, że wątek jest zablokowany dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="06f0f-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06f0f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06f0f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f0f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06f0f-115">Requirements</span></span>  
 <span data-ttu-id="06f0f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f0f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f0f-117">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="06f0f-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="06f0f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06f0f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06f0f-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f0f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f0f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06f0f-120">See also</span></span>

- [<span data-ttu-id="06f0f-121">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="06f0f-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="06f0f-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="06f0f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
