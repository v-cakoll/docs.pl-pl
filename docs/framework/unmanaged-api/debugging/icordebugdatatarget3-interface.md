---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223046"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="01d17-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="01d17-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="01d17-103">Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="01d17-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="01d17-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="01d17-104">Method</span></span>  
  
|<span data-ttu-id="01d17-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01d17-105">Method</span></span>|<span data-ttu-id="01d17-106">Opis</span><span class="sxs-lookup"><span data-stu-id="01d17-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01d17-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="01d17-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="01d17-108">Pobiera listę modułów, które zostały załadowane do tej pory.</span><span class="sxs-lookup"><span data-stu-id="01d17-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d17-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01d17-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01d17-110">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01d17-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="01d17-111">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="01d17-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d17-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01d17-112">Requirements</span></span>  
 <span data-ttu-id="01d17-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01d17-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d17-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01d17-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01d17-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01d17-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01d17-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d17-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d17-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01d17-117">See also</span></span>

- [<span data-ttu-id="01d17-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01d17-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="01d17-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="01d17-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
