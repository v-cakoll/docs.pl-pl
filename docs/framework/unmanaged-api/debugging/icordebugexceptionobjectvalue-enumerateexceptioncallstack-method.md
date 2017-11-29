---
title: "ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue.EnumerateExceptionCallStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue::EnumerateExceptionCallStack
helpviewer_keywords:
- EnumerateExceptionCallStack method, ICorDebugExceptionObjectValue interface [.NET Framework debugging]
- ICorDebugExceptionObjectValue::EnumerateExceptionCallStack method [.NET Framework debugging]
ms.assetid: 00c64533-15dd-47f4-bb97-fe80a1ebadef
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 861d2ad5f9ce0fcc11ea7b1743cd369235cbd878
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalueenumerateexceptioncallstack-method"></a><span data-ttu-id="a09c5-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack — Metoda</span><span class="sxs-lookup"><span data-stu-id="a09c5-102">ICorDebugExceptionObjectValue::EnumerateExceptionCallStack Method</span></span>
<span data-ttu-id="a09c5-103">Pobiera moduł wyliczający stos wywołań osadzonego w obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a09c5-103">Gets an enumerator to the call stack embedded in an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09c5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a09c5-104">Syntax</span></span>  
  
```  
HRESULT EnumerateExceptionCallStack(  
    [out] ICorDebugExceptionObjectCallStackEnum **ppCallStackEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a09c5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a09c5-105">Parameters</span></span>  
 <span data-ttu-id="a09c5-106">ppCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="a09c5-106">ppCallStackEnum</span></span>  
 <span data-ttu-id="a09c5-107">[out] Wskaźnik do adresu [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) obiektu interfejsu, który moduł śledzenia stosu wyjątków zarządzanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="a09c5-107">[out] A pointer to the address of an [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) interface object that is a stack trace enumerator for a managed exception object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a09c5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a09c5-108">Remarks</span></span>  
 <span data-ttu-id="a09c5-109">Jeśli informacje stosu wywołań są niedostępne, metoda zwraca `S_OK`, i [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) jest prawidłowym modułem wyliczającym o długości 0.</span><span class="sxs-lookup"><span data-stu-id="a09c5-109">If no call stack information is available, the method returns `S_OK`, and [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) is a valid enumerator with a length of 0.</span></span> <span data-ttu-id="a09c5-110">Jeśli metoda nie może pobrać informacje śledzenia stosu, jest zwracana wartość `E_FAIL` i nie modułu wyliczającego są zwracane.</span><span class="sxs-lookup"><span data-stu-id="a09c5-110">If the method is unable to retrieve stack trace information, the return value is `E_FAIL` and no enumerator is returned.</span></span>  
  
 <span data-ttu-id="a09c5-111">[ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) obiektu jest odpowiedzialny za dekodowania danych śledzenia stosu z `_stackTrace` pole obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a09c5-111">The [ICorDebugExceptionObjectCallStackEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md) object is responsible for decoding the stack trace data from the `_stackTrace` field of the exception object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09c5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a09c5-112">Requirements</span></span>  
 <span data-ttu-id="a09c5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09c5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09c5-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a09c5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a09c5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a09c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a09c5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09c5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a09c5-117">See Also</span></span>  
 [<span data-ttu-id="a09c5-118">ICorDebugExceptionObjectValue — interfejs</span><span class="sxs-lookup"><span data-stu-id="a09c5-118">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 [<span data-ttu-id="a09c5-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a09c5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
