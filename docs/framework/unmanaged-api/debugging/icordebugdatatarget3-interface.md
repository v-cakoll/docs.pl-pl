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
ms.openlocfilehash: a1ab94e792265916e29ed24239e25cb5d57d1313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="38455-102">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="38455-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="38455-103">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="38455-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="38455-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="38455-104">Method</span></span>  
  
|<span data-ttu-id="38455-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38455-105">Method</span></span>|<span data-ttu-id="38455-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38455-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38455-107">GetLoadedModules — metoda</span><span class="sxs-lookup"><span data-stu-id="38455-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="38455-108">Pobiera listę modułów, które zostały załadowane do tej pory.</span><span class="sxs-lookup"><span data-stu-id="38455-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38455-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38455-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38455-110">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="38455-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="38455-111">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="38455-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38455-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38455-112">Requirements</span></span>  
 <span data-ttu-id="38455-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38455-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38455-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38455-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38455-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38455-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38455-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38455-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38455-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38455-117">See Also</span></span>  
 [<span data-ttu-id="38455-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="38455-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="38455-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38455-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
