---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150530"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="70386-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="70386-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="70386-103">Wskazuje rodzaj zdarzeń, to `ICorDebugDebugEvent` obiekt reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="70386-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70386-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70386-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70386-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70386-105">Parameters</span></span>  
 <span data-ttu-id="70386-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="70386-106">pDebugEventKind</span></span>  
 <span data-ttu-id="70386-107">Wskaźnik do [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) składowej wyliczenia, która określa typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="70386-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70386-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70386-108">Remarks</span></span>  
 <span data-ttu-id="70386-109">Na podstawie wartości z `pDebugEventKind`, można wywołać `QueryInterface` uzyskanie bardziej precyzyjne interfejsu zdarzenia debugowania, która zawiera dane dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="70386-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70386-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="70386-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70386-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70386-111">Requirements</span></span>  
 <span data-ttu-id="70386-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70386-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70386-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70386-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70386-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70386-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70386-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="70386-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70386-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70386-116">See also</span></span>

- [<span data-ttu-id="70386-117">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="70386-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="70386-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="70386-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
