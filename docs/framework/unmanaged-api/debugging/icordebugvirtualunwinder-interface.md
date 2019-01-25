---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684148"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="ca2a9-102">ICorDebugVirtualUnwinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="ca2a9-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="ca2a9-103">Dostarcza metody pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca2a9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca2a9-104">Methods</span></span>  
  
|<span data-ttu-id="ca2a9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca2a9-105">Method</span></span>|<span data-ttu-id="ca2a9-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ca2a9-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="ca2a9-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="ca2a9-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="ca2a9-108">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="ca2a9-109">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="ca2a9-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="ca2a9-110">Przechodzi do obiektu wywołującego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca2a9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca2a9-111">Remarks</span></span>  
 <span data-ttu-id="ca2a9-112">Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera pomagające w wykonywania operacji odwijania stosu.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca2a9-113">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ca2a9-114">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="ca2a9-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca2a9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ca2a9-115">Requirements</span></span>  
 <span data-ttu-id="ca2a9-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca2a9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca2a9-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca2a9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca2a9-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca2a9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca2a9-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca2a9-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2a9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca2a9-120">See also</span></span>
- [<span data-ttu-id="ca2a9-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ca2a9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ca2a9-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ca2a9-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
