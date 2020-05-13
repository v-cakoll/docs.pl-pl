---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 6be216741e902b15efc3a3ece95cb4a4229960e3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212853"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="f3502-102">Metoda ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="f3502-102">ICorDebugProcess6::ProcessStateChanged Method</span></span>
<span data-ttu-id="f3502-103">Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f3502-103">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3502-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3502-104">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3502-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3502-105">Parameters</span></span>  
 `change`  
 <span data-ttu-id="f3502-106">podczas Składowa wyliczenia [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="f3502-106">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3502-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3502-107">Remarks</span></span>  
 <span data-ttu-id="f3502-108">Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](icordebug-interface.md) , że proces jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="f3502-108">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3502-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f3502-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3502-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3502-110">Requirements</span></span>  
 <span data-ttu-id="f3502-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3502-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3502-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3502-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3502-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3502-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3502-114">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3502-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3502-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3502-115">See also</span></span>

- [<span data-ttu-id="f3502-116">Interfejs ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="f3502-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="f3502-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f3502-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
