---
title: Interfejs ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1945e678dd62f81c698807714d0e71053d6b378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414788"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="46d24-102">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="46d24-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="46d24-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="46d24-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="46d24-104">Logicznie rozszerza interfejs ICorDebugFunction zapewnienie dostępu do kodu z żądań ReJIT.</span><span class="sxs-lookup"><span data-stu-id="46d24-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46d24-105">Metody</span><span class="sxs-lookup"><span data-stu-id="46d24-105">Methods</span></span>  
  
|<span data-ttu-id="46d24-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="46d24-106">Method</span></span>|<span data-ttu-id="46d24-107">Opis</span><span class="sxs-lookup"><span data-stu-id="46d24-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46d24-108">GetActiveReJitRequestILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="46d24-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="46d24-109">Pobiera wskaźnika interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="46d24-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d24-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46d24-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d24-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46d24-111">Requirements</span></span>  
 <span data-ttu-id="46d24-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d24-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46d24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46d24-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46d24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46d24-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d24-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46d24-116">See Also</span></span>  
 [<span data-ttu-id="46d24-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="46d24-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="46d24-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="46d24-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="46d24-119">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="46d24-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
