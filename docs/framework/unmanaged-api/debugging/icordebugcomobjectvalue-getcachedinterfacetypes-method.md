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
ms.openlocfilehash: 6b02657012870de4d0f888f6c05b115b25073fa2
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892832"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="83e9a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="83e9a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="83e9a-103">Dostarcza moduł wyliczający dla typów interfejsów, do których rzutuje bieżący obiekt lub którego używał.</span><span class="sxs-lookup"><span data-stu-id="83e9a-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e9a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83e9a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83e9a-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="83e9a-106">podczas Wartość wskazująca, czy metoda zwraca tylko środowisko wykonawcze systemu Windows interfejsy (`IInspectable` interfejsy) czy wszystkie interfejsy com buforowane przez otokę, która umożliwia wywoływanie (RCW) środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="83e9a-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="83e9a-107">określoną Wskaźnik do adresu modułu wyliczającego ICorDebugTypeEnum, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują buforowane typy interfejsów filtrowane zgodnie z `bIInspectableOnly`parametrem.</span><span class="sxs-lookup"><span data-stu-id="83e9a-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e9a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83e9a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e9a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83e9a-109">Requirements</span></span>  
 <span data-ttu-id="83e9a-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e9a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e9a-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="83e9a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e9a-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="83e9a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e9a-113">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e9a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e9a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83e9a-114">See also</span></span>

- [<span data-ttu-id="83e9a-115">ICorDebugComObjectValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="83e9a-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="83e9a-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="83e9a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
