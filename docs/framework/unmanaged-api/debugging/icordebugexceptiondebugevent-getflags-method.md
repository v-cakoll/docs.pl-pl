---
title: 'ICorDebugExceptionDebugEvent:: GetFlags — Metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 5793d939c8497ef842f614048707f69faa8ac568
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976047"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="31a62-102">ICorDebugExceptionDebugEvent:: GetFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="31a62-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="31a62-103">Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="31a62-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31a62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31a62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31a62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31a62-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="31a62-106">określoną Wskaźnik do wartości [CorDebugExceptionFlags —](cordebugexceptionflags-enumeration.md) , który wskazuje, czy można przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="31a62-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31a62-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31a62-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31a62-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="31a62-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31a62-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31a62-109">Requirements</span></span>  
 <span data-ttu-id="31a62-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31a62-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31a62-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31a62-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31a62-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="31a62-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31a62-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31a62-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31a62-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31a62-114">See also</span></span>

- [<span data-ttu-id="31a62-115">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="31a62-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="31a62-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="31a62-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
