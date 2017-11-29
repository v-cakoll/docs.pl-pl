---
title: "ICorDebugExceptionObjectValue — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 47733a6af18d42d0d9db1e50cf21646289ef1443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="59f30-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="59f30-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="59f30-103">Rozszerzenie interfejsu "ICorDebugObjectValue", aby podać informacje śledzenia stosu z obiektem zarządzanym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59f30-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59f30-104">Metody</span><span class="sxs-lookup"><span data-stu-id="59f30-104">Methods</span></span>  
  
|<span data-ttu-id="59f30-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="59f30-105">Method</span></span>|<span data-ttu-id="59f30-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59f30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59f30-107">EnumerateExceptionCallStack — metoda</span><span class="sxs-lookup"><span data-stu-id="59f30-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="59f30-108">Pobiera moduł wyliczający stos wywołań osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59f30-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59f30-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59f30-109">Remarks</span></span>  
 <span data-ttu-id="59f30-110">Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które pochodzą z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59f30-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59f30-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59f30-111">Requirements</span></span>  
 <span data-ttu-id="59f30-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59f30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59f30-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59f30-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59f30-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59f30-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59f30-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59f30-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f30-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59f30-116">See Also</span></span>  
 [<span data-ttu-id="59f30-117">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="59f30-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="59f30-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="59f30-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
