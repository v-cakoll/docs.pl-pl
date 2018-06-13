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
ms.openlocfilehash: 09f1bc2ae9d56eeb6a6242c32d14bf950684d69d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415616"
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="0b68c-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b68c-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="0b68c-103">Pobiera moduł wyliczający stos wywołań osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0b68c-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b68c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b68c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b68c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b68c-105">Parameters</span></span>  
 <span data-ttu-id="0b68c-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="0b68c-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="0b68c-107">[out] Wskaźnik do adresu [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) obiektu interfejsu, który moduł śledzenia stosu wyjątków zarządzanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="0b68c-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b68c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b68c-108">Remarks</span></span>  
 <span data-ttu-id="0b68c-109">Jeśli informacje stosu wywołań są niedostępne, metoda zwraca `S_OK`, i [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) jest prawidłowym modułem wyliczającym o długości 0.</span><span class="sxs-lookup"><span data-stu-id="0b68c-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="0b68c-110">Jeśli metoda nie może pobrać informacje śledzenia stosu, jest zwracana wartość `E_FAIL` i nie modułu wyliczającego są zwracane.</span><span class="sxs-lookup"><span data-stu-id="0b68c-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="0b68c-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) obiektu jest odpowiedzialny za dekodowania danych śledzenia stosu z `_stackTrace` pole obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="0b68c-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b68c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b68c-112">Requirements</span></span>  
 <span data-ttu-id="0b68c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b68c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b68c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b68c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b68c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b68c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b68c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b68c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b68c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b68c-117">See Also</span></span>  
 [<span data-ttu-id="0b68c-118">ICorDebugExceptionObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b68c-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="0b68c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0b68c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
