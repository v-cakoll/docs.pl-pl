---
title: Metoda ICorDebugDebugEvent::GetEventKind
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
ms.openlocfilehash: 0c67f8bdce49b4e9200b501aaf00ae293cced7d7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783413"
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="aab38-102">Metoda ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="aab38-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="aab38-103">Wskazuje, jaki rodzaj zdarzenia reprezentuje ten obiekt `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="aab38-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aab38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aab38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aab38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aab38-105">Parameters</span></span>  
 <span data-ttu-id="aab38-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="aab38-106">pDebugEventKind</span></span>  
 <span data-ttu-id="aab38-107">Wskaźnik do elementu członkowskiego wyliczenia [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) , który wskazuje typ zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aab38-107">A pointer to a [CorDebugDebugEventKind](cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aab38-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aab38-108">Remarks</span></span>  
 <span data-ttu-id="aab38-109">Na podstawie wartości `pDebugEventKind`można wywołać `QueryInterface`, aby uzyskać dokładniejszy interfejs zdarzenia debugowania z dodatkowymi danymi.</span><span class="sxs-lookup"><span data-stu-id="aab38-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aab38-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="aab38-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aab38-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aab38-111">Requirements</span></span>  
 <span data-ttu-id="aab38-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aab38-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aab38-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aab38-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aab38-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aab38-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aab38-115">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aab38-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab38-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aab38-116">See also</span></span>

- [<span data-ttu-id="aab38-117">ICorDebugDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="aab38-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="aab38-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="aab38-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
