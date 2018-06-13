---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5b4a15f637526cd2faadd2d9d3da143c40140f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414908"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="7a462-102">Metoda ICorDebugDebugEvent::GetThread</span><span class="sxs-lookup"><span data-stu-id="7a462-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="7a462-103">Pobiera wątku, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7a462-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a462-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a462-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a462-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a462-105">Parameters</span></span>  
 <span data-ttu-id="7a462-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="7a462-106">ppThread</span></span>  
 <span data-ttu-id="7a462-107">[out] Wskaźnik do adresu ICorDebugThread obiekt, który reprezentuje wątku, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7a462-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a462-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a462-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a462-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7a462-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a462-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a462-110">Requirements</span></span>  
 <span data-ttu-id="7a462-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a462-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a462-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a462-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a462-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a462-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a462-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a462-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a462-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a462-115">See Also</span></span>  
 [<span data-ttu-id="7a462-116">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="7a462-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="7a462-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7a462-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
