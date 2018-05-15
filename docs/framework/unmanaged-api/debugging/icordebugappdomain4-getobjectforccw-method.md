---
title: ICorDebugAppDomain4::GetObjectForCCW — metoda
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1089668aa19747f5f694360ebb87098e2df9ad4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="9e257-102">ICorDebugAppDomain4::GetObjectForCCW — metoda</span><span class="sxs-lookup"><span data-stu-id="9e257-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="9e257-103">Pobiera obiekt zarządzany ze wskaźnika wywoływana otoka (CCW) COM.</span><span class="sxs-lookup"><span data-stu-id="9e257-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e257-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e257-104">Syntax</span></span>  
  
```  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e257-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e257-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="9e257-106">[in] Wywoływana otoka (CCW) wskaźnika COM.</span><span class="sxs-lookup"><span data-stu-id="9e257-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="9e257-107">[out] Wskaźnik do adresu obiektu "ICorDebugValue", który reprezentuje obiekt zarządzany, do którego odnosi się do danego wskaźnika w lewo.</span><span class="sxs-lookup"><span data-stu-id="9e257-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e257-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e257-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e257-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e257-109">Requirements</span></span>  
 <span data-ttu-id="9e257-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e257-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e257-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e257-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e257-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e257-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e257-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e257-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e257-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e257-114">See Also</span></span>  
 [<span data-ttu-id="9e257-115">ICorDebugAppDomain4, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e257-115">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 [<span data-ttu-id="9e257-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9e257-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
