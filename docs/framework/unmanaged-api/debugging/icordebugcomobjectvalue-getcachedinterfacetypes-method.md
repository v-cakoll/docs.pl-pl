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
ms.openlocfilehash: f720b06581ac60c8bd68dc5e85f15843fd9425f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788906"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="12d49-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="12d49-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="12d49-103">Dostarcza moduł wyliczający dla typów interfejsów, do których rzutuje bieżący obiekt lub którego używał.</span><span class="sxs-lookup"><span data-stu-id="12d49-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12d49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12d49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12d49-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="12d49-106">podczas Wartość wskazująca, czy metoda zwraca tylko interfejsy środowisko wykonawcze systemu Windows (interfejsy`IInspectable`) lub wszystkie interfejsy COM buforowane przez otokę, która umożliwia wywoływanie (OTOKa) środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="12d49-106">[in] A value that indicates whether the method returns only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="12d49-107">określoną Wskaźnik do adresu modułu wyliczającego ICorDebugTypeEnum, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują buforowane typy interfejsów filtrowane według `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="12d49-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12d49-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12d49-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12d49-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12d49-109">Requirements</span></span>  
 <span data-ttu-id="12d49-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12d49-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d49-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12d49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12d49-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="12d49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12d49-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d49-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12d49-114">See also</span></span>

- [<span data-ttu-id="12d49-115">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="12d49-115">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="12d49-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="12d49-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
