---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62eede48eea01563dbc3e170720694a24343d0a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150530"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="8c3f0-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="8c3f0-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="8c3f0-103">Wskazuje rodzaj zdarzeń, to `ICorDebugDebugEvent` obiekt reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="8c3f0-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c3f0-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c3f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c3f0-105">Parameters</span></span>  
 <span data-ttu-id="8c3f0-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="8c3f0-106">pDebugEventKind</span></span>  
 <span data-ttu-id="8c3f0-107">Wskaźnik do [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) składowej wyliczenia, która określa typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8c3f0-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c3f0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c3f0-108">Remarks</span></span>  
 <span data-ttu-id="8c3f0-109">Na podstawie wartości z `pDebugEventKind`, można wywołać `QueryInterface` uzyskanie bardziej precyzyjne interfejsu zdarzenia debugowania, która zawiera dane dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="8c3f0-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c3f0-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8c3f0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c3f0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c3f0-111">Requirements</span></span>  
 <span data-ttu-id="8c3f0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3f0-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c3f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c3f0-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c3f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c3f0-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3f0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3f0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c3f0-116">See also</span></span>

- [<span data-ttu-id="8c3f0-117">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c3f0-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [<span data-ttu-id="8c3f0-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c3f0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
