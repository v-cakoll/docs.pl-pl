---
title: CorDebugExceptionFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: 198de0aed4e229d7ed8bb1679afc3a0102bd5368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098465"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="49cc7-102">CorDebugExceptionFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="49cc7-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="49cc7-103">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="49cc7-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cc7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49cc7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="49cc7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="49cc7-105">Members</span></span>  
  
|<span data-ttu-id="49cc7-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="49cc7-106">Member</span></span>|<span data-ttu-id="49cc7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="49cc7-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="49cc7-108">Nie istnieje żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="49cc7-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="49cc7-109">Wyjątek jest przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="49cc7-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="49cc7-110">Czas wyjątku może być nadal taki, aby debuger nie mógł go przechwycić.</span><span class="sxs-lookup"><span data-stu-id="49cc7-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="49cc7-111">Na przykład, jeśli nie istnieje kod zarządzany poniżej bieżącego wywołania zwrotnego lub zdarzenie wyjątku spowodowało z załącznika just-in-Time (JIT), nie można przechwycić wyjątku.</span><span class="sxs-lookup"><span data-stu-id="49cc7-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49cc7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="49cc7-112">Remarks</span></span>  
 <span data-ttu-id="49cc7-113">Nowe wartości można dodać do tego wyliczenia w nowszych wersjach, dlatego należy przygotować kod, który używa `CorDebugExceptionFlags` dla nieoczekiwanych wartości.</span><span class="sxs-lookup"><span data-stu-id="49cc7-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49cc7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49cc7-114">Requirements</span></span>  
 <span data-ttu-id="49cc7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49cc7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49cc7-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49cc7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49cc7-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49cc7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49cc7-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49cc7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cc7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49cc7-119">See also</span></span>

- [<span data-ttu-id="49cc7-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="49cc7-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
