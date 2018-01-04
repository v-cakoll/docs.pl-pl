---
title: Interfejs ICorDebugStaticFieldSymbol
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="31ebe-102">Interfejs ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="31ebe-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="31ebe-103">Reprezentuje informacje symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="31ebe-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31ebe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="31ebe-104">Methods</span></span>  
  
|<span data-ttu-id="31ebe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="31ebe-105">Method</span></span>|<span data-ttu-id="31ebe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="31ebe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31ebe-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="31ebe-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="31ebe-108">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="31ebe-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="31ebe-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="31ebe-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="31ebe-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="31ebe-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="31ebe-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="31ebe-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="31ebe-112">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="31ebe-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31ebe-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31ebe-113">Remarks</span></span>  
 <span data-ttu-id="31ebe-114">`ICorDebugStaticFieldSymbol` Interfejs służy do pobierania informacji o symbolach debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="31ebe-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31ebe-115">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="31ebe-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="31ebe-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="31ebe-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ebe-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31ebe-117">Requirements</span></span>  
 <span data-ttu-id="31ebe-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31ebe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ebe-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31ebe-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31ebe-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31ebe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31ebe-121">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ebe-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ebe-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31ebe-122">See Also</span></span>  
 [<span data-ttu-id="31ebe-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="31ebe-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="31ebe-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="31ebe-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="31ebe-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="31ebe-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
