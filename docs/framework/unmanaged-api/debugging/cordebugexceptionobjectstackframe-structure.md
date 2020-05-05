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
ms.openlocfilehash: 7eccaf984b187e463195bb3804f87bbb2c7ad47b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795927"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="bb078-102">CorDebugExceptionObjectStackFrame — Struktura</span><span class="sxs-lookup"><span data-stu-id="bb078-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="bb078-103">Reprezentuje informacje o ramce stosu z obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="bb078-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb078-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb078-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="bb078-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bb078-105">Members</span></span>  
  
|<span data-ttu-id="bb078-106">Członek</span><span class="sxs-lookup"><span data-stu-id="bb078-106">Member</span></span>|<span data-ttu-id="bb078-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bb078-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="bb078-108">Wskaźnik do obiektu ICorDebugModule dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="bb078-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="bb078-109">Wartość wskaźnika instrukcji (EIP/RIP) dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="bb078-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="bb078-110">Token metody dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="bb078-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="bb078-111">Wartość wskazująca, czy ramka jest ostatnią ramką w wyjątku obcym.</span><span class="sxs-lookup"><span data-stu-id="bb078-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb078-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb078-112">Remarks</span></span>  
 <span data-ttu-id="bb078-113">Obiekt wywołujący musi zwolnić wskaźnik do obiektu ICorDebugModule, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="bb078-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb078-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb078-114">Requirements</span></span>  
 <span data-ttu-id="bb078-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb078-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb078-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bb078-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb078-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb078-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb078-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb078-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb078-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb078-119">See also</span></span>

- [<span data-ttu-id="bb078-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="bb078-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="bb078-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bb078-121">Debugging</span></span>](index.md)
