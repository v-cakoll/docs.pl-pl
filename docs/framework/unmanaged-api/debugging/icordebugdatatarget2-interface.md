---
title: Interfejs ICorDebugDataTarget2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 034e7d46c1b38aecdab18ea3a7d3b149b3d59369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="f1edb-102">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="f1edb-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="f1edb-103">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f1edb-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1edb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f1edb-104">Methods</span></span>  
  
|<span data-ttu-id="f1edb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1edb-105">Method</span></span>|<span data-ttu-id="f1edb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f1edb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1edb-107">Metoda CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="f1edb-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="f1edb-108">Tworzy nowy unwinder stosu, uruchamiany rozwinięcia z kontekstu początkowej (co jest zawsze typu liść wątku).</span><span class="sxs-lookup"><span data-stu-id="f1edb-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="f1edb-109">Metoda EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="f1edb-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="f1edb-110">Zwraca listę aktywnych wątku identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="f1edb-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="f1edb-111">Metoda GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="f1edb-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="f1edb-112">Zwraca adres podstawowy modułu i rozmiaru z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="f1edb-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="f1edb-113">Metoda GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="f1edb-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="f1edb-114">Zwraca ścieżkę modułu z adresem podstawowym modułu.</span><span class="sxs-lookup"><span data-stu-id="f1edb-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="f1edb-115">Metoda GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="f1edb-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="f1edb-116">Zwraca dostawcę symboli dla modułu z adresu podstawowego przestrzeni tego modułu.</span><span class="sxs-lookup"><span data-stu-id="f1edb-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1edb-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1edb-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1edb-118">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f1edb-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="f1edb-119">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="f1edb-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1edb-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1edb-120">Requirements</span></span>  
 <span data-ttu-id="f1edb-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1edb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1edb-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1edb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1edb-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1edb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1edb-124">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1edb-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1edb-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1edb-125">See Also</span></span>  
 [<span data-ttu-id="f1edb-126">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f1edb-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f1edb-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f1edb-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
