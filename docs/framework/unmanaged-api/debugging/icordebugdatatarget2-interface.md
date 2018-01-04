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
ms.workload: dotnet
ms.openlocfilehash: 2aefdb34277d2cb7ebc29ef817745b85064475d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="b8c8e-102">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="b8c8e-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="b8c8e-103">Rozszerza logicznie [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8c8e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b8c8e-104">Methods</span></span>  
  
|<span data-ttu-id="b8c8e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-105">Method</span></span>|<span data-ttu-id="b8c8e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b8c8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8c8e-107">CreateVirtualUnwinder, metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="b8c8e-108">Tworzy nowy unwinder stosu, uruchamiany rozwinięcia z kontekstu początkowej (co jest zawsze typu liść wątku).</span><span class="sxs-lookup"><span data-stu-id="b8c8e-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="b8c8e-109">EnumerateThreadIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="b8c8e-110">Zwraca listę aktywnych wątku identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="b8c8e-111">GetImageFromPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="b8c8e-112">Zwraca adres podstawowy modułu i rozmiaru z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="b8c8e-113">GetImageLocation, metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="b8c8e-114">Zwraca ścieżkę modułu z adresem podstawowym modułu.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="b8c8e-115">GetSymbolProviderForImage, metoda</span><span class="sxs-lookup"><span data-stu-id="b8c8e-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="b8c8e-116">Zwraca dostawcę symboli dla modułu z adresu podstawowego przestrzeni tego modułu.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8c8e-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8c8e-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8c8e-118">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b8c8e-119">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b8c8e-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8c8e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8c8e-120">Requirements</span></span>  
 <span data-ttu-id="b8c8e-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8c8e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8c8e-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8c8e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8c8e-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8c8e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8c8e-124">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8c8e-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c8e-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8c8e-125">See Also</span></span>  
 [<span data-ttu-id="b8c8e-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8c8e-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b8c8e-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b8c8e-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
