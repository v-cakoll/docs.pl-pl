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
ms.openlocfilehash: 4c29d631f84ce2dd7532e32951e71d6597218ebb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088863"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="122ac-102">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="122ac-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="122ac-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="122ac-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="122ac-104">Rozszerza logicznie ICorDebugFunction — interfejs w celu zapewnienia dostępu do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="122ac-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="122ac-105">Metody</span><span class="sxs-lookup"><span data-stu-id="122ac-105">Methods</span></span>  
  
|<span data-ttu-id="122ac-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="122ac-106">Method</span></span>|<span data-ttu-id="122ac-107">Opis</span><span class="sxs-lookup"><span data-stu-id="122ac-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="122ac-108">GetActiveReJitRequestILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="122ac-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="122ac-109">Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="122ac-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="122ac-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="122ac-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122ac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="122ac-111">Requirements</span></span>  
 <span data-ttu-id="122ac-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122ac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122ac-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="122ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="122ac-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="122ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="122ac-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122ac-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="122ac-116">See also</span></span>

- [<span data-ttu-id="122ac-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="122ac-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="122ac-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="122ac-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="122ac-119">ReJIT: Przewodniku z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="122ac-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
