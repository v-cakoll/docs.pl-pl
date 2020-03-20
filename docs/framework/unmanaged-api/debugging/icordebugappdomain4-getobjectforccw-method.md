---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179047"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="44cff-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="44cff-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="44cff-103">Pobiera obiekt zarządzany ze wskaźnika otoki wywoływanej com (CCW).</span><span class="sxs-lookup"><span data-stu-id="44cff-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44cff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44cff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44cff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44cff-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="44cff-106">[w] Wskaźnik otoki wywoływanej com (CCW).</span><span class="sxs-lookup"><span data-stu-id="44cff-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="44cff-107">[na zewnątrz] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje obiekt zarządzany, który odpowiada podanemu wskaźnikowi CCW.</span><span class="sxs-lookup"><span data-stu-id="44cff-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44cff-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44cff-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44cff-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44cff-109">Requirements</span></span>  
 <span data-ttu-id="44cff-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44cff-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44cff-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44cff-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44cff-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44cff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44cff-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44cff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44cff-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44cff-114">See also</span></span>

- [<span data-ttu-id="44cff-115">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="44cff-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="44cff-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="44cff-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
