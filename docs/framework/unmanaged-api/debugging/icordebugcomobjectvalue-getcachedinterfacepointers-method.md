---
title: "ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2b47395235ce21c7d40e4413702e6c655493a739
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="d7313-102">ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7313-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="d7313-103">Pobiera wskaźniki interfejsu pierwotnego, buforowane na bieżącym wywoływana otoka środowiska uruchomieniowego (otoki RCW).</span><span class="sxs-lookup"><span data-stu-id="d7313-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7313-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7313-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7313-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7313-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="d7313-106">[in] Wartość, która wskazuje, czy metoda zwróci tylko [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfejsów (`IInspectable` interfejsów) lub wszystkich interfejsów modelu COM, które nie są buforowane przez wywoływana otoka środowiska uruchomieniowego (otoki RCW).</span><span class="sxs-lookup"><span data-stu-id="d7313-106">[in] A value that indicates whether the method will return only [!INCLUDE[wrt](../../../../includes/wrt-md.md)] interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="d7313-107">[in] Liczba obiektów, których adresy mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="d7313-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d7313-108">[out] Wskaźnik do liczby `CORDB_ADDRESS` wartości zwracanych w rzeczywistości w `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="d7313-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="d7313-109">Wskaźnik do adres początkowy tablicę `CORDB_ADDRESS` wartości, które zawierają adresy interfejsu obiektów w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="d7313-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7313-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7313-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7313-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7313-111">Requirements</span></span>  
 <span data-ttu-id="d7313-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7313-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7313-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7313-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7313-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7313-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7313-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7313-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7313-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7313-116">See Also</span></span>  
 [<span data-ttu-id="d7313-117">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7313-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 [<span data-ttu-id="d7313-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d7313-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
