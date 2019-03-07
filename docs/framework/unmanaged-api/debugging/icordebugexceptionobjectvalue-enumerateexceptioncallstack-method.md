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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e168c1a520ca0159ab273dcf9b56b41b4f32b4e4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497148"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="b501e-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda</span><span class="sxs-lookup"><span data-stu-id="b501e-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="b501e-103">Pobiera moduł wyliczający do stosu wywołań, osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b501e-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b501e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b501e-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b501e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b501e-105">Parameters</span></span>  
 <span data-ttu-id="b501e-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b501e-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="b501e-107">[out] Wskaźnik na adres [icordebugexceptionobjectcallstackenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interfejsu obiekt modułu wyliczającego ślad stosu dla zarządzanego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b501e-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b501e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b501e-108">Remarks</span></span>  
 <span data-ttu-id="b501e-109">Jeśli nie informacje stosu wywołań jest dostępna, metoda zwraca `S_OK`, i [icordebugexceptionobjectcallstackenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) jest prawidłowym modułem wyliczającym z długość 0.</span><span class="sxs-lookup"><span data-stu-id="b501e-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="b501e-110">Jeśli metoda nie może pobrać informacje o śladzie stosu, wartość zwracana jest `E_FAIL` i zostanie zwrócony nie modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b501e-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="b501e-111">[Icordebugexceptionobjectcallstackenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) obiektu jest odpowiedzialny za dekodowania danych śledzenia stosu z obiektu `_stackTrace` pola obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b501e-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b501e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b501e-112">Requirements</span></span>  
 <span data-ttu-id="b501e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b501e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b501e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b501e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b501e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b501e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b501e-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b501e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b501e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b501e-117">See also</span></span>
- [<span data-ttu-id="b501e-118">ICorDebugExceptionObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="b501e-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)
- [<span data-ttu-id="b501e-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b501e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
