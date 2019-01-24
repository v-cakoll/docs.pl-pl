---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d674159b33cad1a77a82e39b9f11a38c98cbd3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687404"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="0d0d5-102">Metoda ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="0d0d5-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="0d0d5-103">Pobiera wątku, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0d0d5-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d0d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d0d5-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d0d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d0d5-105">Parameters</span></span>  
 <span data-ttu-id="0d0d5-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="0d0d5-106">ppThread</span></span>  
 <span data-ttu-id="0d0d5-107">[out] Wskaźnik na adres ICorDebugThread obiekt, który reprezentuje wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0d0d5-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d0d5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d0d5-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d0d5-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0d0d5-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d0d5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d0d5-110">Requirements</span></span>  
 <span data-ttu-id="0d0d5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d0d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d0d5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d0d5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d0d5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d0d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d0d5-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d0d5-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d0d5-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d0d5-115">See also</span></span>
- [<span data-ttu-id="0d0d5-116">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d0d5-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="0d0d5-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0d0d5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
