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
ms.openlocfilehash: badd79926e8f039cf6b947dd6655e2cd679e3000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406978"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="47245-102">CorDebugSetContextFlag — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="47245-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="47245-103">Wskazuje, czy kontekst jest z aktywnego (lub typu liść) ramek na stosie lub został obliczony przy odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="47245-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47245-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47245-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="47245-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="47245-105">Members</span></span>  
  
|<span data-ttu-id="47245-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="47245-106">Member</span></span>|<span data-ttu-id="47245-107">Opis</span><span class="sxs-lookup"><span data-stu-id="47245-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="47245-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="47245-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="47245-109">Kontekst jest aktywny kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="47245-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="47245-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="47245-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="47245-111">Kontekst został obliczony przy odwijanie od innej ramki.</span><span class="sxs-lookup"><span data-stu-id="47245-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47245-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47245-112">Remarks</span></span>  
 <span data-ttu-id="47245-113">`CorDebugSetContextFlag` udostępnia wartości, które są używane przez [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="47245-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47245-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47245-114">Requirements</span></span>  
 <span data-ttu-id="47245-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47245-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47245-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47245-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47245-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47245-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47245-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47245-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47245-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47245-119">See Also</span></span>  
 [<span data-ttu-id="47245-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="47245-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="47245-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="47245-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
