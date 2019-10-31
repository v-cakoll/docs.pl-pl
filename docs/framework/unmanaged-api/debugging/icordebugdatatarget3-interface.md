---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 5f91db291396589a916933bdc7c2a2390dd61a5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136666"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="f524f-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="f524f-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="f524f-103">Logicznie rozszerza interfejs [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) w celu dostarczenia informacji o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="f524f-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="f524f-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="f524f-104">Method</span></span>  
  
|<span data-ttu-id="f524f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f524f-105">Method</span></span>|<span data-ttu-id="f524f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f524f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f524f-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="f524f-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="f524f-108">Pobiera listę modułów, które zostały wcześniej załadowane.</span><span class="sxs-lookup"><span data-stu-id="f524f-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f524f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f524f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f524f-110">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f524f-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f524f-111">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="f524f-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f524f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f524f-112">Requirements</span></span>  
 <span data-ttu-id="f524f-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f524f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f524f-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f524f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f524f-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f524f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f524f-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f524f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f524f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f524f-117">See also</span></span>

- [<span data-ttu-id="f524f-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f524f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f524f-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f524f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
