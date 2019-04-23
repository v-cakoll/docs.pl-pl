---
title: Metoda ICorDebugVirtualUnwinder::Next
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74be827dc97213507b96da9e025923f859011acd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076890"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="f93e9-102">Metoda ICorDebugVirtualUnwinder::Next</span><span class="sxs-lookup"><span data-stu-id="f93e9-102">ICorDebugVirtualUnwinder::Next Method</span></span>
<span data-ttu-id="f93e9-103">Przechodzi do obiektu wywołującego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="f93e9-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f93e9-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="f93e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f93e9-105">Parameters</span></span>  
 <span data-ttu-id="f93e9-106">Brak.</span><span class="sxs-lookup"><span data-stu-id="f93e9-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f93e9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f93e9-107">Return Value</span></span>  
 <span data-ttu-id="f93e9-108">`S_OK` Jeśli rozwinięcie wystąpił pomyślnie, lub `CORDBG_S_AT_END_OF_STACK` Jeśli rozwinięcie nie można zakończyć, ponieważ nie ma żadnych więcej ramek.</span><span class="sxs-lookup"><span data-stu-id="f93e9-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="f93e9-109">Jeśli niepowodzenie, jest zwracana wartość HRESULT, icordebug — interfejsy API zwracają `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="f93e9-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f93e9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f93e9-110">Remarks</span></span>  
 <span data-ttu-id="f93e9-111">Walker stosu należy upewnić się, że to sprawia, że postęp, to znaczy po pewnym czasie wywołania `Next` zwróci niepowodzenie HRESULT lub `CORDBG_S_AT_END_OF_STACK`.</span><span class="sxs-lookup"><span data-stu-id="f93e9-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="f93e9-112">Zwracanie `S_OK` przez czas nieokreślony może spowodować nieskończoną pętlę.</span><span class="sxs-lookup"><span data-stu-id="f93e9-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f93e9-113">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f93e9-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93e9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f93e9-114">Requirements</span></span>  
 <span data-ttu-id="f93e9-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93e9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93e9-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f93e9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f93e9-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f93e9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f93e9-118">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93e9-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93e9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f93e9-119">See also</span></span>

- [<span data-ttu-id="f93e9-120">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="f93e9-120">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="f93e9-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f93e9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
