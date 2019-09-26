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
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273973"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="430d2-102">CorDebugBlockingObject — Struktura</span><span class="sxs-lookup"><span data-stu-id="430d2-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="430d2-103">Definiuje obiekt, który blokuje wątek i konkretną przyczynę zablokowania wątku.</span><span class="sxs-lookup"><span data-stu-id="430d2-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="430d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="430d2-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="430d2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="430d2-105">Members</span></span>  
  
|<span data-ttu-id="430d2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="430d2-106">Member</span></span>|<span data-ttu-id="430d2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="430d2-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="430d2-108">Obiekt, na którym jest blokowany wątek.</span><span class="sxs-lookup"><span data-stu-id="430d2-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="430d2-109">Ten obiekt jest prawidłowy tylko dla czasu trwania bieżącego zsynchronizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="430d2-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="430d2-110">Jeśli dwa wątki blokują ten sam obiekt w tym samym stanie zsynchronizowanym, można oczekiwać, że metoda [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) zwraca tę samą wartość.</span><span class="sxs-lookup"><span data-stu-id="430d2-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="430d2-111">Jednak interfejsy mogą lub nie mogą być odpowiednikami wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="430d2-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="430d2-112">Liczba milisekund przed upływem limitu czasu operacji blokowania lub wartość NIESKOŃCZONość, która wskazuje, że nie przekroczy limitu czasu. Wartość limitu czasu określa łączny czas trwania operacji blokowania, a nie czas, który jest nadal pozostały.</span><span class="sxs-lookup"><span data-stu-id="430d2-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="430d2-113">Przyczyna blokowania wątku dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="430d2-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="430d2-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="430d2-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="430d2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="430d2-115">Requirements</span></span>  
 <span data-ttu-id="430d2-116">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="430d2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="430d2-117">**Nagłówki** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="430d2-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="430d2-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="430d2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="430d2-119">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="430d2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430d2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="430d2-120">See also</span></span>

- [<span data-ttu-id="430d2-121">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="430d2-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="430d2-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="430d2-122">Debugging</span></span>](index.md)
