---
title: Metoda ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208842"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="5f2c2-102">Metoda ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="5f2c2-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="5f2c2-103">Pobiera flagę wskazującą, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="5f2c2-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f2c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f2c2-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f2c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f2c2-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="5f2c2-106">[out] Wskaźnik do [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wartość, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="5f2c2-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f2c2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f2c2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f2c2-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5f2c2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f2c2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f2c2-109">Requirements</span></span>  
 <span data-ttu-id="5f2c2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f2c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f2c2-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f2c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f2c2-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f2c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f2c2-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f2c2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2c2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f2c2-114">See also</span></span>

- [<span data-ttu-id="5f2c2-115">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f2c2-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="5f2c2-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5f2c2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
