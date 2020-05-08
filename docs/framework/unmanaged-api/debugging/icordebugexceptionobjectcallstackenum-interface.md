---
title: ICorDebugExceptionObjectCallStackEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975995"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="c003d-102">ICorDebugExceptionObjectCallStackEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c003d-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="c003d-103">Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c003d-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="c003d-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c003d-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c003d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c003d-105">Methods</span></span>  
  
|<span data-ttu-id="c003d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c003d-106">Method</span></span>|<span data-ttu-id="c003d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c003d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c003d-108">ICorDebugExceptionObjectCallStackEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="c003d-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="c003d-109">Pobiera określoną liczbę obiektów [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) , które zawierają informacje o stosie wywołań obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c003d-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c003d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c003d-110">Remarks</span></span>  
 <span data-ttu-id="c003d-111">`ICorDebugExceptionObjectCallStackEnum` Interfejs implementuje interfejs ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="c003d-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="c003d-112">`ICorDebugExceptionObjectCallStackEnum` Wystąpienie jest wypełniane obiektami [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) przez wywołanie metody [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack —](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c003d-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="c003d-113">Elementy stosu wywołań w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="c003d-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c003d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c003d-114">Requirements</span></span>  
 <span data-ttu-id="c003d-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c003d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c003d-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c003d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c003d-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c003d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c003d-118">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c003d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c003d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c003d-119">See also</span></span>

- [<span data-ttu-id="c003d-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c003d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c003d-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c003d-121">Debugging</span></span>](index.md)
