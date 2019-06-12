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
ms.openlocfilehash: e1da347fd85e1b3856615faf49c60b607cc7f0da
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025838"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="def65-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="def65-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="def65-103">Dostarcza moduł wyliczający dla typów interfejsu, czy bieżący obiekt został rzutować lub używany jako.</span><span class="sxs-lookup"><span data-stu-id="def65-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def65-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="def65-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="def65-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="def65-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="def65-106">[in] Wartość, która wskazuje, czy metoda ta zwraca tylko interfejsów Windows Runtime (`IInspectable` interfejsów) lub wszystkie interfejsy COM, buforowane przez otoka wywoływana w czasie wykonywania (RCW).</span><span class="sxs-lookup"><span data-stu-id="def65-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="def65-107">[out] Wskaźnik na adres icordebugtypeenum — moduł wyliczający, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują typy interfejsu w pamięci podręcznej filtrowane zgodnie z opisem w `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="def65-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="def65-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="def65-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="def65-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="def65-109">Requirements</span></span>  
 <span data-ttu-id="def65-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="def65-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="def65-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="def65-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="def65-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="def65-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="def65-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="def65-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def65-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="def65-114">See also</span></span>

- [<span data-ttu-id="def65-115">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="def65-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="def65-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="def65-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
