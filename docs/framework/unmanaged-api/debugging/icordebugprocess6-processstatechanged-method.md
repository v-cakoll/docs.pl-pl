---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792202"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="edf2e-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="edf2e-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="edf2e-103">Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="edf2e-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edf2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edf2e-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edf2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edf2e-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="edf2e-106">podczas Składowa wyliczenia [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="edf2e-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edf2e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edf2e-107">Remarks</span></span>  
 <span data-ttu-id="edf2e-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](icordebug-interface.md) , że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="edf2e-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edf2e-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="edf2e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edf2e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edf2e-110">Requirements</span></span>  
 <span data-ttu-id="edf2e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edf2e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edf2e-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="edf2e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edf2e-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="edf2e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edf2e-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edf2e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edf2e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edf2e-115">See also</span></span>

- [<span data-ttu-id="edf2e-116">ICorDebugProcess6, interfejs</span><span class="sxs-lookup"><span data-stu-id="edf2e-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="edf2e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="edf2e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
