---
title: ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77e7f20aba1908a63d77b4ccada7fabacf55f7
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025851"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="a4b89-102">ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4b89-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="a4b89-103">Pobiera wskaźniki interfejsu raw, buforowane na bieżącym wywoływana otoka środowiska uruchomieniowego (RCW).</span><span class="sxs-lookup"><span data-stu-id="a4b89-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4b89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4b89-104">Syntax</span></span>  
  
```  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4b89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4b89-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="a4b89-106">[in] Wartość, która wskazuje, czy metoda zwróci tylko interfejsów Windows Runtime (`IInspectable` interfejsów) lub wszystkie interfejsy COM, które są buforowane przez otoka wywoływana w czasie wykonywania (RCW).</span><span class="sxs-lookup"><span data-stu-id="a4b89-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="a4b89-107">[in] Liczba obiektów, których adresy, które mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="a4b89-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a4b89-108">[out] Wskaźnik do liczby `CORDB_ADDRESS` wartości zwracanych w rzeczywistości w `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="a4b89-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="a4b89-109">Wskaźnik do tablicy adres początkowy `CORDB_ADDRESS` wartości, które zawierają adresy pamięci podręcznej obiektów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a4b89-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4b89-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4b89-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b89-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4b89-111">Requirements</span></span>  
 <span data-ttu-id="a4b89-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b89-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b89-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4b89-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4b89-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4b89-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4b89-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b89-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b89-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4b89-116">See also</span></span>

- [<span data-ttu-id="a4b89-117">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="a4b89-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="a4b89-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a4b89-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
