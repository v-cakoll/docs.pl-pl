---
title: ICorDebugExceptionDebugEvent::GetFlags — metoda
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b9c07b010447b4a437febb4b60565111a85c8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="426db-102">ICorDebugExceptionDebugEvent::GetFlags — metoda</span><span class="sxs-lookup"><span data-stu-id="426db-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="426db-103">Pobiera flagę wskazującą, czy wyjątek może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="426db-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="426db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="426db-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="426db-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="426db-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="426db-106">[out] Wskaźnik do [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wartość, która wskazuje, czy wyjątek może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="426db-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="426db-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="426db-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="426db-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="426db-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="426db-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="426db-109">Requirements</span></span>  
 <span data-ttu-id="426db-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="426db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="426db-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="426db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="426db-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="426db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="426db-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="426db-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="426db-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="426db-114">See Also</span></span>  
 [<span data-ttu-id="426db-115">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="426db-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="426db-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="426db-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
