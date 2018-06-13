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
ms.openlocfilehash: d6805b7b49f76b80161aef5051fe3c284192f582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413777"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="360b2-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="360b2-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="360b2-103">Rozszerzenie interfejsu "ICorDebugObjectValue", aby podać informacje śledzenia stosu z obiektem zarządzanym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="360b2-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="360b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="360b2-104">Methods</span></span>  
  
|<span data-ttu-id="360b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="360b2-105">Method</span></span>|<span data-ttu-id="360b2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="360b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="360b2-107">EnumerateExceptionCallStack, metoda</span><span class="sxs-lookup"><span data-stu-id="360b2-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="360b2-108">Pobiera moduł wyliczający stos wywołań osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="360b2-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="360b2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="360b2-109">Remarks</span></span>  
 <span data-ttu-id="360b2-110">Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które pochodzą z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="360b2-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360b2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="360b2-111">Requirements</span></span>  
 <span data-ttu-id="360b2-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="360b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360b2-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="360b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="360b2-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="360b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="360b2-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360b2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="360b2-116">See Also</span></span>  
 [<span data-ttu-id="360b2-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="360b2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="360b2-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="360b2-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
