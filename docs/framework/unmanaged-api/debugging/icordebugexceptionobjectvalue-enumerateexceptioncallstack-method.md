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
ms.openlocfilehash: 57eb284bfe39ce92b2d6c03a2aeb4ae84d6aba91
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788669"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="ee246-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee246-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="ee246-103">Pobiera moduł wyliczający w stosie wywołań osadzonym w obiekcie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="ee246-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee246-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee246-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee246-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee246-105">Parameters</span></span>  
 <span data-ttu-id="ee246-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="ee246-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="ee246-107">określoną Wskaźnik do adresu obiektu interfejsu [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) , który jest modułem wyliczania śladu stosu dla obiektu wyjątku zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="ee246-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee246-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee246-108">Remarks</span></span>  
 <span data-ttu-id="ee246-109">Jeśli żadne informacje stosu wywołań nie są dostępne, metoda zwraca `S_OK`, a [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) jest prawidłowym modułem wyliczającym o długości 0.</span><span class="sxs-lookup"><span data-stu-id="ee246-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="ee246-110">Jeśli metoda nie może pobrać informacji o śledzeniu stosu, zwracana wartość jest `E_FAIL` i żaden moduł wyliczający nie jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="ee246-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="ee246-111">Obiekt [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) jest odpowiedzialny za dekodowanie danych śledzenia stosu z pola `_stackTrace` obiektu Exception.</span><span class="sxs-lookup"><span data-stu-id="ee246-111">The [ICorDebugExceptionObjectCallStackEnum](icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee246-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee246-112">Requirements</span></span>  
 <span data-ttu-id="ee246-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee246-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee246-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee246-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee246-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ee246-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee246-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee246-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee246-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee246-117">See also</span></span>

- [<span data-ttu-id="ee246-118">ICorDebugExceptionObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee246-118">ICorDebugExceptionObjectValue Interface</span></span>](icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="ee246-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ee246-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
