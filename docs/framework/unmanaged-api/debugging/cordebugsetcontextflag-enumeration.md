---
title: CorDebugSetContextFlag — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e959ce7a77ad6ceb7f2fc848193cbd9fff028279
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739617"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="20ec5-102">CorDebugSetContextFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="20ec5-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="20ec5-103">Wskazuje, czy kontekst jest z aktywnej (lub liścia) ramek na stosie lub obliczeniu, odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="20ec5-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ec5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20ec5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="20ec5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="20ec5-105">Members</span></span>  
  
|<span data-ttu-id="20ec5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="20ec5-106">Member</span></span>|<span data-ttu-id="20ec5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20ec5-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20ec5-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="20ec5-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="20ec5-109">Kontekst jest aktywny kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="20ec5-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="20ec5-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="20ec5-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="20ec5-111">Kontekst ma zostać obliczone przez odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="20ec5-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20ec5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20ec5-112">Remarks</span></span>  
 <span data-ttu-id="20ec5-113">`CorDebugSetContextFlag` zawiera wartości, które są używane przez [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="20ec5-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ec5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="20ec5-114">Requirements</span></span>  
 <span data-ttu-id="20ec5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20ec5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20ec5-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="20ec5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="20ec5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20ec5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20ec5-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20ec5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ec5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20ec5-119">See also</span></span>

- [<span data-ttu-id="20ec5-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="20ec5-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="20ec5-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="20ec5-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
