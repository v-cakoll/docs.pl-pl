---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87dda8d8a263df1989a685d94c5163212f41382
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911338"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="b1acc-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="b1acc-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="b1acc-103">Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="b1acc-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1acc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1acc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1acc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1acc-105">Parameters</span></span>  
 <span data-ttu-id="b1acc-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="b1acc-106">pDebugEventKind</span></span>  
 <span data-ttu-id="b1acc-107">Wskaźnik do elementu członkowskiego wyliczenia [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) , który wskazuje typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b1acc-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1acc-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1acc-108">Remarks</span></span>  
 <span data-ttu-id="b1acc-109">Na podstawie wartości `pDebugEventKind`, można wywołać `QueryInterface` , aby uzyskać dokładniejszy interfejs zdarzenia debugowania, który zawiera dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="b1acc-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1acc-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b1acc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1acc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1acc-111">Requirements</span></span>  
 <span data-ttu-id="b1acc-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1acc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1acc-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1acc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1acc-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1acc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1acc-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1acc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1acc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1acc-116">See also</span></span>

- [<span data-ttu-id="b1acc-117">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1acc-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="b1acc-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b1acc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
