---
title: Metoda ICorDebugExceptionDebugEvent::GetFlags
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af4c7feb7076eeac6089a3255c7832c17a43469b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208842"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="bbff7-102">Metoda ICorDebugExceptionDebugEvent::GetFlags</span><span class="sxs-lookup"><span data-stu-id="bbff7-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="bbff7-103">Pobiera flagę wskazującą, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="bbff7-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbff7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbff7-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbff7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbff7-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="bbff7-106">[out] Wskaźnik do [cordebugexceptionflags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wartość, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="bbff7-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbff7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbff7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bbff7-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bbff7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbff7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bbff7-109">Requirements</span></span>  
 <span data-ttu-id="bbff7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbff7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbff7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbff7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbff7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbff7-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bbff7-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bbff7-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbff7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbff7-114">See also</span></span>

- [<span data-ttu-id="bbff7-115">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bbff7-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="bbff7-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="bbff7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
