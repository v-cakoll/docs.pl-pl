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
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788661"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="217d8-102">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="217d8-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="217d8-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="217d8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="217d8-104">Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia dostępu do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="217d8-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="217d8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="217d8-105">Methods</span></span>  
  
|<span data-ttu-id="217d8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="217d8-106">Method</span></span>|<span data-ttu-id="217d8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="217d8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="217d8-108">GetActiveReJitRequestILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="217d8-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="217d8-109">Pobiera wskaźnik interfejsu do [ICorDebugILCode](icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="217d8-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="217d8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="217d8-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="217d8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="217d8-111">Requirements</span></span>  
 <span data-ttu-id="217d8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="217d8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="217d8-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="217d8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="217d8-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="217d8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="217d8-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="217d8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217d8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="217d8-116">See also</span></span>

- [<span data-ttu-id="217d8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="217d8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="217d8-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="217d8-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="217d8-119">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="217d8-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
