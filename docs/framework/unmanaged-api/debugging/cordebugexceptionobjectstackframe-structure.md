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
ms.openlocfilehash: 2845c15d67e287d6efb0cd0a9c940b69de3a1c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789376"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="0ee56-102">CorDebugExceptionObjectStackFrame — Struktura</span><span class="sxs-lookup"><span data-stu-id="0ee56-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="0ee56-103">Reprezentuje informacje o ramce stosu z obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="0ee56-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ee56-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="0ee56-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0ee56-105">Members</span></span>  
  
|<span data-ttu-id="0ee56-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0ee56-106">Member</span></span>|<span data-ttu-id="0ee56-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0ee56-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="0ee56-108">Wskaźnik do obiektu ICorDebugModule dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="0ee56-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="0ee56-109">Wartość wskaźnika instrukcji (EIP/RIP) dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="0ee56-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="0ee56-110">Token metody dla bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="0ee56-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="0ee56-111">Wartość wskazująca, czy ramka jest ostatnią ramką w wyjątku obcym.</span><span class="sxs-lookup"><span data-stu-id="0ee56-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ee56-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ee56-112">Remarks</span></span>  
 <span data-ttu-id="0ee56-113">Obiekt wywołujący musi zwolnić wskaźnik do obiektu ICorDebugModule, gdy nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="0ee56-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee56-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ee56-114">Requirements</span></span>  
 <span data-ttu-id="0ee56-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ee56-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ee56-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0ee56-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ee56-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0ee56-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ee56-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ee56-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee56-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ee56-119">See also</span></span>

- [<span data-ttu-id="0ee56-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="0ee56-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0ee56-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0ee56-121">Debugging</span></span>](index.md)
