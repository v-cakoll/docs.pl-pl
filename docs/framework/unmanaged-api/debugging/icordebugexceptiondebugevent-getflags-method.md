---
title: Metoda ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739b2412d6b75df0921f778c95cc2fe65fef9b79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636043"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="2915b-102">Metoda ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="2915b-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="2915b-103">Pobiera flagę wskazującą, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="2915b-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2915b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2915b-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2915b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2915b-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="2915b-106">[out] Wskaźnik do [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wartość, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="2915b-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2915b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2915b-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2915b-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2915b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2915b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2915b-109">Requirements</span></span>  
 <span data-ttu-id="2915b-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2915b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2915b-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2915b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2915b-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2915b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2915b-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2915b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2915b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2915b-114">See also</span></span>
- [<span data-ttu-id="2915b-115">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="2915b-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="2915b-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2915b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
