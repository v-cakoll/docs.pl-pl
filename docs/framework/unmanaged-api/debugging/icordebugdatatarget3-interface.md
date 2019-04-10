---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223046"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="2ecb2-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="2ecb2-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="2ecb2-103">Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="2ecb2-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="2ecb2-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ecb2-104">Method</span></span>  
  
|<span data-ttu-id="2ecb2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ecb2-105">Method</span></span>|<span data-ttu-id="2ecb2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2ecb2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ecb2-107">GetLoadedModules, metoda</span><span class="sxs-lookup"><span data-stu-id="2ecb2-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="2ecb2-108">Pobiera listę modułów, które zostały załadowane do tej pory.</span><span class="sxs-lookup"><span data-stu-id="2ecb2-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ecb2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ecb2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ecb2-110">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ecb2-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="2ecb2-111">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="2ecb2-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ecb2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ecb2-112">Requirements</span></span>  
 <span data-ttu-id="2ecb2-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ecb2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ecb2-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ecb2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ecb2-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ecb2-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2ecb2-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2ecb2-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2ecb2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ecb2-117">See also</span></span>

- [<span data-ttu-id="2ecb2-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ecb2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2ecb2-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2ecb2-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
