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
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="e07eb-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="e07eb-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="e07eb-103">To wskazuje jakiego rodzaju zdarzenia `ICorDebugDebugEvent` reprezentuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="e07eb-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e07eb-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e07eb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e07eb-105">Parameters</span></span>  
 <span data-ttu-id="e07eb-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="e07eb-106">pDebugEventKind</span></span>  
 <span data-ttu-id="e07eb-107">Wskaźnik do [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) element członkowski wyliczenia wskazująca typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e07eb-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e07eb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e07eb-108">Remarks</span></span>  
 <span data-ttu-id="e07eb-109">Na podstawie wartości z `pDebugEventKind`, można wywołać `QueryInterface` uzyskanie dokładniejszej interfejsu zdarzenia debugowania, zawierający dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="e07eb-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e07eb-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e07eb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07eb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e07eb-111">Requirements</span></span>  
 <span data-ttu-id="e07eb-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e07eb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07eb-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e07eb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e07eb-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e07eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e07eb-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07eb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07eb-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e07eb-116">See Also</span></span>  
 [<span data-ttu-id="e07eb-117">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="e07eb-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="e07eb-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e07eb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
