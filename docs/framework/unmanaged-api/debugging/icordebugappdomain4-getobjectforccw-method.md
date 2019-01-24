---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eeb0b80ba691d813e3193f7ae746129c6725e1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506540"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="4b1e6-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="4b1e6-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="4b1e6-103">Pobiera obiekt zarządzany ze wskaźnika wywoływalnej otoki (CCW) COM.</span><span class="sxs-lookup"><span data-stu-id="4b1e6-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b1e6-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b1e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b1e6-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="4b1e6-106">[in] Wywoływana otoka (CCW) wskaźnik COM.</span><span class="sxs-lookup"><span data-stu-id="4b1e6-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="4b1e6-107">[out] Wskaźnik na adres obiektu "ICorDebugValue", który reprezentuje obiektu zarządzanego, który odnosi się do danego wskaźnika w lewo.</span><span class="sxs-lookup"><span data-stu-id="4b1e6-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b1e6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b1e6-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b1e6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b1e6-109">Requirements</span></span>  
 <span data-ttu-id="4b1e6-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b1e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b1e6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b1e6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b1e6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b1e6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b1e6-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b1e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1e6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b1e6-114">See also</span></span>
- [<span data-ttu-id="4b1e6-115">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="4b1e6-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)
- [<span data-ttu-id="4b1e6-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4b1e6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
