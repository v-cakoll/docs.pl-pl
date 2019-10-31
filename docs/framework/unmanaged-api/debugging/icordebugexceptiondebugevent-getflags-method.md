---
title: 'ICorDebugExceptionDebugEvent:: GetFlags — Metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 6c330ce5b375daacdf257eda16fd5e34012f5d69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084752"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="b407d-102">ICorDebugExceptionDebugEvent:: GetFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="b407d-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="b407d-103">Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="b407d-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b407d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b407d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b407d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b407d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="b407d-106">określoną Wskaźnik do wartości [CorDebugExceptionFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) , który wskazuje, czy można przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b407d-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b407d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b407d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b407d-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b407d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b407d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b407d-109">Requirements</span></span>  
 <span data-ttu-id="b407d-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b407d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b407d-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b407d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b407d-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b407d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b407d-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b407d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b407d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b407d-114">See also</span></span>

- [<span data-ttu-id="b407d-115">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b407d-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="b407d-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b407d-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
