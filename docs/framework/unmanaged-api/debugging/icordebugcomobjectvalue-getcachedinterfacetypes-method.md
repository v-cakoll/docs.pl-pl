---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7325e84d8fe4df9a31543426c6376d0941306fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748450"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="195b5-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="195b5-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="195b5-103">Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został rzutować lub używany jako.</span><span class="sxs-lookup"><span data-stu-id="195b5-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="195b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="195b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="195b5-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="195b5-106">[in] Wartość, która wskazuje, czy metoda ta zwraca tylko interfejsów Windows Runtime (`IInspectable` interfejsów) lub wszystkie interfejsy COM, buforowane przez otoka wywoływana w czasie wykonywania (RCW).</span><span class="sxs-lookup"><span data-stu-id="195b5-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="195b5-107">[out] Wskaźnik na adres icordebugtypeenum — moduł wyliczający, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują typy interfejsu w pamięci podręcznej filtrowane zgodnie z opisem w `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="195b5-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="195b5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="195b5-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="195b5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="195b5-109">Requirements</span></span>  
 <span data-ttu-id="195b5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="195b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="195b5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="195b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="195b5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="195b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="195b5-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="195b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195b5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="195b5-114">See also</span></span>

- [<span data-ttu-id="195b5-115">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="195b5-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="195b5-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="195b5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
