---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25bb63f1b1fa759cd6d61a71682b803e3320f22d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="f7342-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="f7342-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="f7342-103">To wskazuje jakiego rodzaju zdarzenia `ICorDebugDebugEvent` reprezentuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="f7342-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7342-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7342-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7342-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7342-105">Parameters</span></span>  
 <span data-ttu-id="f7342-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="f7342-106">pDebugEventKind</span></span>  
 <span data-ttu-id="f7342-107">Wskaźnik do [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) element członkowski wyliczenia wskazująca typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7342-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7342-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7342-108">Remarks</span></span>  
 <span data-ttu-id="f7342-109">Na podstawie wartości z `pDebugEventKind`, można wywołać `QueryInterface` uzyskanie dokładniejszej interfejsu zdarzenia debugowania, zawierający dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="f7342-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7342-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f7342-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7342-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7342-111">Requirements</span></span>  
 <span data-ttu-id="f7342-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7342-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7342-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7342-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7342-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7342-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7342-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7342-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7342-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7342-116">See Also</span></span>  
 [<span data-ttu-id="f7342-117">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7342-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="f7342-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f7342-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
