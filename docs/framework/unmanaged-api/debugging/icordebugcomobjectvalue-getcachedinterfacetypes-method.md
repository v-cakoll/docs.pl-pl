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
ms.openlocfilehash: 199f58456e64ccf7ef771d42d5c7d64b189cb670
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125501"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="9d832-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d832-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="9d832-103">Dostarcza moduł wyliczający dla typów interfejsów, do których rzutuje bieżący obiekt lub którego używał.</span><span class="sxs-lookup"><span data-stu-id="9d832-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d832-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d832-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d832-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="9d832-106">podczas Wartość wskazująca, czy metoda zwraca tylko interfejsy środowisko wykonawcze systemu Windows (interfejsy`IInspectable`) lub wszystkie interfejsy COM buforowane przez otokę, która umożliwia wywoływanie (OTOKa) środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9d832-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="9d832-107">określoną Wskaźnik do adresu modułu wyliczającego ICorDebugTypeEnum, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują buforowane typy interfejsów filtrowane według `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="9d832-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d832-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d832-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d832-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d832-109">Requirements</span></span>  
 <span data-ttu-id="9d832-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d832-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d832-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d832-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d832-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d832-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d832-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d832-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d832-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d832-114">See also</span></span>

- [<span data-ttu-id="9d832-115">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="9d832-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="9d832-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d832-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
