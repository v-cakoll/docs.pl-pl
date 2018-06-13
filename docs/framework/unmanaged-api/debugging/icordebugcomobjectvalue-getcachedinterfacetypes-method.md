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
ms.openlocfilehash: db1de215eaa0c0cc7021a119e54591caede76d3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417128"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a><span data-ttu-id="8b35a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b35a-102">ICorDebugComObjectValue::GetCachedInterfaceTypes Method</span></span>
<span data-ttu-id="8b35a-103">Udostępnia moduł wyliczający dla typów interfejsu, czy bieżący obiekt został rzutować lub używane jako.</span><span class="sxs-lookup"><span data-stu-id="8b35a-103">Provides an enumerator for the interface types that the current object has been cast to or used as.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b35a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b35a-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b35a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b35a-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="8b35a-106">[in] Wartość, która wskazuje, czy metoda zwraca tylko [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfejsów (`IInspectable` interfejsów) lub wszystkie interfejsy modelu COM, wywoływana otoka środowiska uruchomieniowego (otoki RCW) w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="8b35a-106">[in] A value that indicates whether the method returns only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces cached by the runtime callable wrapper (RCW).</span></span>  
  
 `ppInterfacesEnum`  
 <span data-ttu-id="8b35a-107">[out] Wskaźnik do adresu moduł wyliczający ICorDebugTypeEnum, który zapewnia dostęp do obiektów ICorDebugType, które reprezentują typy buforowanych interfejsu filtrowane zgodnie z `bIInspectableOnly`.</span><span class="sxs-lookup"><span data-stu-id="8b35a-107">[out] A pointer to the address of an ICorDebugTypeEnum enumerator that provides access to ICorDebugType objects that represent cached interface types filtered according to `bIInspectableOnly`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b35a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b35a-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b35a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b35a-109">Requirements</span></span>  
 <span data-ttu-id="8b35a-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b35a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b35a-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b35a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b35a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b35a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b35a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b35a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b35a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b35a-114">See Also</span></span>  
 [<span data-ttu-id="8b35a-115">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b35a-115">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="8b35a-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8b35a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
