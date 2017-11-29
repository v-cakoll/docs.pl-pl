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
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="2a818-102">CorDebugExceptionObjectStackFrame — Struktura</span><span class="sxs-lookup"><span data-stu-id="2a818-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="2a818-103">Reprezentuje stosu ramki informacji z obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2a818-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a818-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a818-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="2a818-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2a818-105">Members</span></span>  
  
|<span data-ttu-id="2a818-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2a818-106">Member</span></span>|<span data-ttu-id="2a818-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2a818-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="2a818-108">Wskaźnik do obiektu ICorDebugModule dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="2a818-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="2a818-109">Wartość wskaźnika instrukcji (element EIP/RIP) dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="2a818-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="2a818-110">Token metody dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="2a818-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="2a818-111">Wartość, która wskazuje, czy ramki jest ostatniej ramki z obcego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2a818-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a818-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a818-112">Remarks</span></span>  
 <span data-ttu-id="2a818-113">Obiekt wywołujący musi zwolnić wskaźnik do obiektu ICorDebugModule, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="2a818-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a818-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a818-114">Requirements</span></span>  
 <span data-ttu-id="2a818-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a818-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a818-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a818-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a818-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a818-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a818-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a818-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a818-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a818-119">See Also</span></span>  
 [<span data-ttu-id="2a818-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="2a818-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="2a818-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2a818-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
