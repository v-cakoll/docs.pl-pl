---
title: "ICorDebugDataTarget3 — interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c65bbfa033a3a585cdcfdb42cdda95f1de4aa412
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="b065a-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="b065a-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="b065a-103">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="b065a-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="b065a-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="b065a-104">Method</span></span>  
  
|<span data-ttu-id="b065a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b065a-105">Method</span></span>|<span data-ttu-id="b065a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b065a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b065a-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="b065a-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="b065a-108">Pobiera listę modułów, które zostały załadowane do tej pory.</span><span class="sxs-lookup"><span data-stu-id="b065a-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b065a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b065a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b065a-110">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b065a-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b065a-111">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b065a-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b065a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b065a-112">Requirements</span></span>  
 <span data-ttu-id="b065a-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b065a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b065a-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b065a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b065a-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b065a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b065a-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b065a-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b065a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b065a-117">See Also</span></span>  
 [<span data-ttu-id="b065a-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b065a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b065a-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b065a-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
