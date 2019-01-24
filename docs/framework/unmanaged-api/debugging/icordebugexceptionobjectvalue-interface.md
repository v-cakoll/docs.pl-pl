---
title: ICorDebugExceptionObjectValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1baae7d7867b0cbb227af72fcc505a5cadfa4df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511639"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="2cf98-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2cf98-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="2cf98-103">Umożliwia rozbudowanie interfejsu "ICorDebugObjectValue", aby zapewnić informacje śledzenia stosu z zarządzanego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cf98-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cf98-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2cf98-104">Methods</span></span>  
  
|<span data-ttu-id="2cf98-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2cf98-105">Method</span></span>|<span data-ttu-id="2cf98-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2cf98-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cf98-107">EnumerateExceptionCallStack, metoda</span><span class="sxs-lookup"><span data-stu-id="2cf98-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="2cf98-108">Pobiera moduł wyliczający do stosu wywołań, osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cf98-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf98-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cf98-109">Remarks</span></span>  
 <span data-ttu-id="2cf98-110">Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które wynikają z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2cf98-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf98-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cf98-111">Requirements</span></span>  
 <span data-ttu-id="2cf98-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf98-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf98-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cf98-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cf98-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cf98-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cf98-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf98-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf98-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cf98-116">See also</span></span>
- [<span data-ttu-id="2cf98-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2cf98-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2cf98-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2cf98-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

