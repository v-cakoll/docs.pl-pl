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
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782735"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="65e2c-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="65e2c-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="65e2c-103">Rozszerza interfejs "ICorDebugObjectValue", aby dostarczyć informacje o śledzeniu stosu z obiektu wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="65e2c-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65e2c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="65e2c-104">Methods</span></span>  
  
|<span data-ttu-id="65e2c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="65e2c-105">Method</span></span>|<span data-ttu-id="65e2c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="65e2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65e2c-107">EnumerateExceptionCallStack, metoda</span><span class="sxs-lookup"><span data-stu-id="65e2c-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="65e2c-108">Pobiera moduł wyliczający w stosie wywołań osadzonym w obiekcie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="65e2c-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65e2c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65e2c-109">Remarks</span></span>  
 <span data-ttu-id="65e2c-110">Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które pochodzą z <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65e2c-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e2c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65e2c-111">Requirements</span></span>  
 <span data-ttu-id="65e2c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e2c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e2c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="65e2c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65e2c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="65e2c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65e2c-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65e2c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65e2c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65e2c-116">See also</span></span>

- [<span data-ttu-id="65e2c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="65e2c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="65e2c-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="65e2c-118">Debugging</span></span>](index.md)
