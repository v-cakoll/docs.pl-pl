---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb04ac42b3cc77db3af53c87efb0d1f1f75da928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421288"
---
# <a name="icordebugvirtualunwinder-interface"></a><span data-ttu-id="50b8f-102">ICorDebugVirtualUnwinder — interfejs</span><span class="sxs-lookup"><span data-stu-id="50b8f-102">ICorDebugVirtualUnwinder Interface</span></span>
<span data-ttu-id="50b8f-103">Udostępnia metody, aby pomóc w odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="50b8f-103">Provides methods to help in stack unwinding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50b8f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="50b8f-104">Methods</span></span>  
  
|<span data-ttu-id="50b8f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="50b8f-105">Method</span></span>|<span data-ttu-id="50b8f-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="50b8f-106">Name</span></span>|  
|------------|----------|  
|[<span data-ttu-id="50b8f-107">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="50b8f-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|<span data-ttu-id="50b8f-108">Pobiera bieżący kontekst tego unwinder.</span><span class="sxs-lookup"><span data-stu-id="50b8f-108">Gets the current context of this unwinder.</span></span>|  
|[<span data-ttu-id="50b8f-109">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="50b8f-109">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|<span data-ttu-id="50b8f-110">Przechodzi do kontekstu obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="50b8f-110">Advances to the caller's context.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50b8f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50b8f-111">Remarks</span></span>  
 <span data-ttu-id="50b8f-112">Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera, aby pomóc w odwijanie stosu.</span><span class="sxs-lookup"><span data-stu-id="50b8f-112">The members of the `ICorDebugVirtualUnwinder` interface are implemented by the debugger to help in stack unwinding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50b8f-113">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="50b8f-113">This interface is available with .NET Native only.</span></span> <span data-ttu-id="50b8f-114">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="50b8f-114">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50b8f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50b8f-115">Requirements</span></span>  
 <span data-ttu-id="50b8f-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50b8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50b8f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50b8f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50b8f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50b8f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50b8f-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50b8f-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b8f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50b8f-120">See Also</span></span>  
 [<span data-ttu-id="50b8f-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="50b8f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="50b8f-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="50b8f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
