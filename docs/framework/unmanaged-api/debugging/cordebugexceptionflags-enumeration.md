---
title: "CorDebugExceptionFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionFlags
helpviewer_keywords: CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b25211c8e7f03cc09e8729abc44af39f0c84259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="ca60e-102">CorDebugExceptionFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ca60e-102">CorDebugExceptionFlags Enumeration</span></span>
<span data-ttu-id="ca60e-103">Zawiera dodatkowe informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ca60e-103">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca60e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca60e-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ca60e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ca60e-105">Members</span></span>  
  
|<span data-ttu-id="ca60e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ca60e-106">Member</span></span>|<span data-ttu-id="ca60e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ca60e-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="ca60e-108">Nie ma żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="ca60e-108">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="ca60e-109">Wyjątek stanowi interceptable.</span><span class="sxs-lookup"><span data-stu-id="ca60e-109">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="ca60e-110">Czas wyjątku może nadal być w taki sposób, że debuger nie może przechwycić go.</span><span class="sxs-lookup"><span data-stu-id="ca60e-110">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="ca60e-111">Na przykład jeśli nie istnieje żaden kod zarządzany poniżej bieżącego wywołania zwrotnego lub zdarzenie wyjątku jest wynikiem just in time (JIT) załącznika, wyjątek nie może zostać przechwycone.</span><span class="sxs-lookup"><span data-stu-id="ca60e-111">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca60e-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca60e-112">Remarks</span></span>  
 <span data-ttu-id="ca60e-113">Nowe wartości mogą zostać dodane do tego wyliczenia w nowszych wersjach, więc należy przygotować kodu korzystającego z `CorDebugExceptionFlags` nieoczekiwane wartości.</span><span class="sxs-lookup"><span data-stu-id="ca60e-113">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca60e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca60e-114">Requirements</span></span>  
 <span data-ttu-id="ca60e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca60e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca60e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca60e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca60e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca60e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca60e-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca60e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca60e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca60e-119">See Also</span></span>  
 [<span data-ttu-id="ca60e-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="ca60e-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
