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
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795680"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="41491-102">CorDebugSetContextFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="41491-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="41491-103">Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="41491-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41491-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41491-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="41491-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41491-105">Members</span></span>  
  
|<span data-ttu-id="41491-106">Członek</span><span class="sxs-lookup"><span data-stu-id="41491-106">Member</span></span>|<span data-ttu-id="41491-107">Opis</span><span class="sxs-lookup"><span data-stu-id="41491-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="41491-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="41491-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="41491-109">Kontekst jest aktywnym kontekstem wątku.</span><span class="sxs-lookup"><span data-stu-id="41491-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="41491-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="41491-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="41491-111">Kontekst został obliczony przez odwinięcia z innej ramki.</span><span class="sxs-lookup"><span data-stu-id="41491-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41491-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41491-112">Remarks</span></span>  
 <span data-ttu-id="41491-113">`CorDebugSetContextFlag`dostarcza wartości, które są używane przez metodę [ICorDebugStackWalk:: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41491-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41491-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41491-114">Requirements</span></span>  
 <span data-ttu-id="41491-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41491-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41491-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41491-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41491-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41491-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41491-118">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41491-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41491-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41491-119">See also</span></span>

- [<span data-ttu-id="41491-120">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="41491-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="41491-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="41491-121">Debugging</span></span>](index.md)
