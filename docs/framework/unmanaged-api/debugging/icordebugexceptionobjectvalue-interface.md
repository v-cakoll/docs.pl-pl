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
ms.openlocfilehash: 8e4f745440936a39e22faf60d10a05a0bb110606
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975956"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="93097-102">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="93097-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="93097-103">Rozszerza interfejs "ICorDebugObjectValue", aby dostarczyć informacje o śledzeniu stosu z obiektu wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="93097-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93097-104">Metody</span><span class="sxs-lookup"><span data-stu-id="93097-104">Methods</span></span>  
  
|<span data-ttu-id="93097-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="93097-105">Method</span></span>|<span data-ttu-id="93097-106">Opis</span><span class="sxs-lookup"><span data-stu-id="93097-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93097-107">EnumerateExceptionCallStack, metoda</span><span class="sxs-lookup"><span data-stu-id="93097-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="93097-108">Pobiera moduł wyliczający w stosie wywołań osadzonym w obiekcie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="93097-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93097-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93097-109">Remarks</span></span>  
 <span data-ttu-id="93097-110">Wywołanie `QueryInterface` powiedzie się dla obiektów zarządzanych, które pochodzą od <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93097-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93097-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93097-111">Requirements</span></span>  
 <span data-ttu-id="93097-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93097-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93097-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93097-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93097-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93097-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93097-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93097-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93097-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93097-116">See also</span></span>

- [<span data-ttu-id="93097-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="93097-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="93097-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="93097-118">Debugging</span></span>](index.md)
