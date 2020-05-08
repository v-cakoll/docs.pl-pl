---
title: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type:
- apiref
ms.openlocfilehash: e45b180ac6d943d89740ad7ae10500ea4ad1aa9c
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975969"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="b7fd0-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7fd0-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="b7fd0-103">Pobiera moduł wyliczający w stosie wywołań osadzonym w obiekcie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b7fd0-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7fd0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7fd0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7fd0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7fd0-105">Parameters</span></span>  
 <span data-ttu-id="b7fd0-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b7fd0-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="b7fd0-107">określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , który jest modułem wyliczania śladu stosu dla obiektu wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b7fd0-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7fd0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7fd0-108">Remarks</span></span>  
 <span data-ttu-id="b7fd0-109">Jeśli żadne informacje stosu wywołań nie są dostępne, metoda zwraca `S_OK`wartość, a [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) jest prawidłowym modułem wyliczającym o długości 0.</span><span class="sxs-lookup"><span data-stu-id="b7fd0-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="b7fd0-110">Jeśli metoda nie może pobrać informacji o śledzeniu stosu, zwracana wartość jest `E_FAIL` i nie jest zwracany żaden moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="b7fd0-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="b7fd0-111">Obiekt [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) jest odpowiedzialny za dekodowanie danych śledzenia stosu z `_stackTrace` pola obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="b7fd0-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7fd0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7fd0-112">Requirements</span></span>  
 <span data-ttu-id="b7fd0-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7fd0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7fd0-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b7fd0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7fd0-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b7fd0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7fd0-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7fd0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7fd0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7fd0-117">See also</span></span>

- [<span data-ttu-id="b7fd0-118">ICorDebugExceptionObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b7fd0-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="b7fd0-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b7fd0-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
