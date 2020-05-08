---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 6e3ebdcb5b3e85f6f5a329ed249aa58be903e30f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976398"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="7fb73-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="7fb73-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="7fb73-103">Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="7fb73-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fb73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fb73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fb73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fb73-105">Parameters</span></span>  
 <span data-ttu-id="7fb73-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="7fb73-106">pDebugEventKind</span></span>  
 <span data-ttu-id="7fb73-107">Wskaźnik do elementu członkowskiego wyliczenia [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , który wskazuje typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7fb73-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fb73-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fb73-108">Remarks</span></span>  
 <span data-ttu-id="7fb73-109">Na podstawie wartości `pDebugEventKind`, można wywołać `QueryInterface` , aby uzyskać dokładniejszy interfejs zdarzenia debugowania, który zawiera dodatkowe dane.</span><span class="sxs-lookup"><span data-stu-id="7fb73-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7fb73-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7fb73-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fb73-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fb73-111">Requirements</span></span>  
 <span data-ttu-id="7fb73-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fb73-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fb73-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7fb73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fb73-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7fb73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fb73-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fb73-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fb73-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fb73-116">See also</span></span>

- [<span data-ttu-id="7fb73-117">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="7fb73-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="7fb73-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7fb73-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
