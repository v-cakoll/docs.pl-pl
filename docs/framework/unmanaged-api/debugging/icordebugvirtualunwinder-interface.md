---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 639cfc514d2a206f0de72db4b0bac02b53305ae3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083403"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="8c090-102">ICorDebugVirtualUnwinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="8c090-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="8c090-103">Dostarcza metody pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="8c090-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c090-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c090-104">Methods</span></span>  
  
|<span data-ttu-id="8c090-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c090-105">Method</span></span>|<span data-ttu-id="8c090-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8c090-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="8c090-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="8c090-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="8c090-108">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="8c090-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="8c090-109">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="8c090-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="8c090-110">Przechodzi do obiektu wywołującego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8c090-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c090-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c090-111">Remarks</span></span>  
 <span data-ttu-id="8c090-112">Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="8c090-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c090-113">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8c090-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8c090-114">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="8c090-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c090-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c090-115">Requirements</span></span>  
 <span data-ttu-id="8c090-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c090-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c090-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c090-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c090-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c090-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8c090-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8c090-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8c090-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c090-120">See also</span></span>

- [<span data-ttu-id="8c090-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c090-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8c090-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8c090-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
