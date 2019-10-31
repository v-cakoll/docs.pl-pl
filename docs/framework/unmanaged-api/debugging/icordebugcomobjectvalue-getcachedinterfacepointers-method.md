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
ms.openlocfilehash: c1e2b557a5e5794c50986b1af8ec39faba845cc9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125514"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="9e7bf-102">ICorDebugComObjectValue::GetCachedInterfacePointers — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e7bf-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="9e7bf-103">Pobiera pierwotne wskaźniki interfejsu w pamięci podręcznej dla bieżącej otoki (RCW) w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9e7bf-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e7bf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e7bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e7bf-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="9e7bf-106">podczas Wartość wskazująca, czy metoda zwróci tylko środowisko wykonawcze systemu Windows interfejsy (`IInspectable` Interfaces) czy wszystkie interfejsy COM, które są buforowane przez otokę wywoływaną przez środowisko uruchomieniowe (OTOKa).</span><span class="sxs-lookup"><span data-stu-id="9e7bf-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="9e7bf-107">podczas Liczba obiektów, których adresy mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="9e7bf-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9e7bf-108">określoną Wskaźnik do liczby wartości `CORDB_ADDRESS` faktycznie zwróconych w `ptrs`.</span><span class="sxs-lookup"><span data-stu-id="9e7bf-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="9e7bf-109">Wskaźnik do adresu początkowego tablicy wartości `CORDB_ADDRESS`, które zawierają adresy buforowanych obiektów interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9e7bf-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e7bf-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e7bf-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7bf-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e7bf-111">Requirements</span></span>  
 <span data-ttu-id="9e7bf-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e7bf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7bf-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9e7bf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e7bf-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e7bf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e7bf-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7bf-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e7bf-116">See also</span></span>

- [<span data-ttu-id="9e7bf-117">ICorDebugComObjectValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e7bf-117">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="9e7bf-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e7bf-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
