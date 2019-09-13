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
ms.openlocfilehash: a3eebdf56796fe599ec6ff62d7008d1af3be796e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926835"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="2ec80-102">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="2ec80-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="2ec80-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2ec80-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="2ec80-104">Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia dostępu do kodu z żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2ec80-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2ec80-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2ec80-105">Methods</span></span>  
  
|<span data-ttu-id="2ec80-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2ec80-106">Method</span></span>|<span data-ttu-id="2ec80-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2ec80-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ec80-108">GetActiveReJitRequestILCode, metoda</span><span class="sxs-lookup"><span data-stu-id="2ec80-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="2ec80-109">Pobiera wskaźnik interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.</span><span class="sxs-lookup"><span data-stu-id="2ec80-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ec80-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ec80-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec80-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ec80-111">Requirements</span></span>  
 <span data-ttu-id="2ec80-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec80-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec80-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ec80-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ec80-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ec80-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ec80-115">**.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec80-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ec80-116">See also</span></span>

- [<span data-ttu-id="2ec80-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ec80-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2ec80-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2ec80-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="2ec80-119">ReJIT: Przewodnik krok po kroku</span><span class="sxs-lookup"><span data-stu-id="2ec80-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
