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
ms.workload: dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="754a8-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="754a8-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="754a8-103">Rozszerzenie interfejsu "ICorDebugObjectValue", aby podać informacje śledzenia stosu z obiektem zarządzanym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="754a8-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="754a8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="754a8-104">Methods</span></span>  
  
|<span data-ttu-id="754a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="754a8-105">Method</span></span>|<span data-ttu-id="754a8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="754a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="754a8-107">EnumerateExceptionCallStack, metoda</span><span class="sxs-lookup"><span data-stu-id="754a8-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="754a8-108">Pobiera moduł wyliczający stos wywołań osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="754a8-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="754a8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="754a8-109">Remarks</span></span>  
 <span data-ttu-id="754a8-110">Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które pochodzą z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="754a8-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="754a8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="754a8-111">Requirements</span></span>  
 <span data-ttu-id="754a8-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="754a8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="754a8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="754a8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="754a8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="754a8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="754a8-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="754a8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="754a8-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="754a8-116">See Also</span></span>  
 [<span data-ttu-id="754a8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="754a8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="754a8-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="754a8-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
