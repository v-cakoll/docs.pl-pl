---
title: CorDebugExceptionObjectStackFrame — Struktura
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4cd4d353c22921ed3dba1dc08fe2cee7e429f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173085"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="cd49d-102">CorDebugExceptionObjectStackFrame — Struktura</span><span class="sxs-lookup"><span data-stu-id="cd49d-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="cd49d-103">Reprezentuje stosu ramki informacje z obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cd49d-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd49d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd49d-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="cd49d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cd49d-105">Members</span></span>  
  
|<span data-ttu-id="cd49d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cd49d-106">Member</span></span>|<span data-ttu-id="cd49d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cd49d-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="cd49d-108">Wskaźnik do obiektu ICorDebugModule dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="cd49d-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="cd49d-109">Wartość wskaźnika instrukcji (EIP/RIP) dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="cd49d-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="cd49d-110">Token metody dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="cd49d-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="cd49d-111">Wartość, która wskazuje, czy ramki jest ostatniej ramki obcego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cd49d-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd49d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd49d-112">Remarks</span></span>  
 <span data-ttu-id="cd49d-113">Obiekt wywołujący musi zwolnić wskaźnik do obiektu ICorDebugModule, gdy nie jest już używana.</span><span class="sxs-lookup"><span data-stu-id="cd49d-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd49d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd49d-114">Requirements</span></span>  
 <span data-ttu-id="cd49d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd49d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd49d-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd49d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd49d-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd49d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd49d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd49d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd49d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd49d-119">See also</span></span>

- [<span data-ttu-id="cd49d-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="cd49d-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="cd49d-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cd49d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
