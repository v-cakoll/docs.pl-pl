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
ms.openlocfilehash: a443332e4f2b0351e99754fae610af39268bb105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789270"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="3c0a4-102">CorDebugSetContextFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3c0a4-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="3c0a4-103">Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c0a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c0a4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="3c0a4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3c0a4-105">Members</span></span>  
  
|<span data-ttu-id="3c0a4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3c0a4-106">Member</span></span>|<span data-ttu-id="3c0a4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3c0a4-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="3c0a4-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="3c0a4-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="3c0a4-109">Kontekst jest aktywnym kontekstem wątku.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="3c0a4-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="3c0a4-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="3c0a4-111">Kontekst został obliczony przez odwinięcia z innej ramki.</span><span class="sxs-lookup"><span data-stu-id="3c0a4-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c0a4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c0a4-112">Remarks</span></span>  
 <span data-ttu-id="3c0a4-113">`CorDebugSetContextFlag` zawiera wartości, które są używane przez metodę [ICorDebugStackWalk:: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3c0a4-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c0a4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c0a4-114">Requirements</span></span>  
 <span data-ttu-id="3c0a4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c0a4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c0a4-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3c0a4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c0a4-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3c0a4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c0a4-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c0a4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c0a4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c0a4-119">See also</span></span>

- [<span data-ttu-id="3c0a4-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="3c0a4-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="3c0a4-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3c0a4-121">Debugging</span></span>](index.md)
