---
title: 'ICorDebugExceptionDebugEvent:: GetFlags — Metoda'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782918"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="2e260-102">ICorDebugExceptionDebugEvent:: GetFlags — Metoda</span><span class="sxs-lookup"><span data-stu-id="2e260-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="2e260-103">Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="2e260-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e260-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e260-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e260-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e260-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="2e260-106">określoną Wskaźnik do wartości [CorDebugExceptionFlags —](cordebugexceptionflags-enumeration.md) , który wskazuje, czy można przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2e260-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e260-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e260-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e260-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2e260-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e260-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e260-109">Requirements</span></span>  
 <span data-ttu-id="2e260-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e260-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e260-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e260-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e260-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2e260-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e260-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e260-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e260-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e260-114">See also</span></span>

- [<span data-ttu-id="2e260-115">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e260-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="2e260-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2e260-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
