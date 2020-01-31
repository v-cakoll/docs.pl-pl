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
ms.openlocfilehash: 6ef81e224f3573021ee96ac313ec4923928dedad
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789399"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="fb5f5-102">CorDebugExceptionFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fb5f5-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="fb5f5-103">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb5f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb5f5-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="fb5f5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fb5f5-105">Members</span></span>  
  
|<span data-ttu-id="fb5f5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fb5f5-106">Member</span></span>|<span data-ttu-id="fb5f5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fb5f5-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="fb5f5-108">Nie istnieje żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="fb5f5-109">Wyjątek jest przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="fb5f5-110">Czas wyjątku może być nadal taki, aby debuger nie mógł go przechwycić.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="fb5f5-111">Na przykład, jeśli nie istnieje kod zarządzany poniżej bieżącego wywołania zwrotnego lub zdarzenie wyjątku spowodowało z załącznika just-in-Time (JIT), nie można przechwycić wyjątku.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb5f5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb5f5-112">Remarks</span></span>  
 <span data-ttu-id="fb5f5-113">Nowe wartości można dodać do tego wyliczenia w nowszych wersjach, dlatego należy przygotować kod, który używa `CorDebugExceptionFlags` dla nieoczekiwanych wartości.</span><span class="sxs-lookup"><span data-stu-id="fb5f5-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb5f5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb5f5-114">Requirements</span></span>  
 <span data-ttu-id="fb5f5-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb5f5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb5f5-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb5f5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb5f5-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fb5f5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb5f5-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb5f5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb5f5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb5f5-119">See also</span></span>

- [<span data-ttu-id="fb5f5-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fb5f5-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
