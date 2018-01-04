---
title: "CorDebugExceptionObjectStackFrame — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f2d3f0d0c17c0fdf8b772ba38ae97fd8e406be8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="f0ea8-102">CorDebugExceptionObjectStackFrame — Struktura</span><span class="sxs-lookup"><span data-stu-id="f0ea8-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="f0ea8-103">Reprezentuje stosu ramki informacji z obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ea8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0ea8-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="f0ea8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f0ea8-105">Members</span></span>  
  
|<span data-ttu-id="f0ea8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f0ea8-106">Member</span></span>|<span data-ttu-id="f0ea8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f0ea8-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="f0ea8-108">Wskaźnik do obiektu ICorDebugModule dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="f0ea8-109">Wartość wskaźnika instrukcji (element EIP/RIP) dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="f0ea8-110">Token metody dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="f0ea8-111">Wartość, która wskazuje, czy ramki jest ostatniej ramki z obcego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0ea8-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0ea8-112">Remarks</span></span>  
 <span data-ttu-id="f0ea8-113">Obiekt wywołujący musi zwolnić wskaźnik do obiektu ICorDebugModule, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="f0ea8-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ea8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0ea8-114">Requirements</span></span>  
 <span data-ttu-id="f0ea8-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0ea8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0ea8-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0ea8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0ea8-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0ea8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0ea8-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0ea8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ea8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0ea8-119">See Also</span></span>  
 [<span data-ttu-id="f0ea8-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="f0ea8-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="f0ea8-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f0ea8-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
