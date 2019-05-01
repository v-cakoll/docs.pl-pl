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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7b9b25673685dde8b75702c80f525515917ae1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915256"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="ab084-102">CorDebugExceptionFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab084-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="ab084-103">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ab084-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab084-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab084-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ab084-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ab084-105">Members</span></span>  
  
|<span data-ttu-id="ab084-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ab084-106">Member</span></span>|<span data-ttu-id="ab084-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ab084-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="ab084-108">Nie ma wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ab084-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="ab084-109">Wyjątek stanowi interceptable.</span><span class="sxs-lookup"><span data-stu-id="ab084-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="ab084-110">Chronometraż wyjątek może nadal być w taki sposób, że debuger nie może przechwycić go.</span><span class="sxs-lookup"><span data-stu-id="ab084-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="ab084-111">Na przykład jeśli żaden kod zarządzany poniżej bieżącego wywołania zwrotnego, lub zdarzenie wyjątku jest wynikiem just-in-time (JIT) załącznika, wyjątek nie mogą zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ab084-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab084-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab084-112">Remarks</span></span>  
 <span data-ttu-id="ab084-113">Nowe wartości mogą być dodawane do tego wyliczenia w nowszych wersjach, więc należy przygotować kod, który używa `CorDebugExceptionFlags` nieoczekiwane wartości.</span><span class="sxs-lookup"><span data-stu-id="ab084-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab084-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab084-114">Requirements</span></span>  
 <span data-ttu-id="ab084-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab084-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab084-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab084-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab084-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab084-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab084-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab084-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab084-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab084-119">See also</span></span>

- [<span data-ttu-id="ab084-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ab084-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
