---
title: Interfejs ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0931cb5ed133d4de82473ae786f28f13fd396db5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743013"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="0bd52-102">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="0bd52-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="0bd52-103">Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0bd52-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bd52-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0bd52-104">Methods</span></span>  
  
|<span data-ttu-id="0bd52-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-105">Method</span></span>|<span data-ttu-id="0bd52-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0bd52-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bd52-107">CreateVirtualUnwinder, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="0bd52-108">Tworzy nowy unwinder stosu, który rozpoczyna się odwijanie od początkowego kontekstu, (które niekoniecznie liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="0bd52-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="0bd52-109">EnumerateThreadIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="0bd52-110">Zwraca listę aktywnych wątków identyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="0bd52-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="0bd52-111">GetImageFromPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="0bd52-112">Zwraca adres podstawowy moduł i rozmiar z adresu w module.</span><span class="sxs-lookup"><span data-stu-id="0bd52-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="0bd52-113">GetImageLocation, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="0bd52-114">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="0bd52-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="0bd52-115">GetSymbolProviderForImage, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd52-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="0bd52-116">Zwraca adres bazowy modułu, dostawca symboli dla modułu.</span><span class="sxs-lookup"><span data-stu-id="0bd52-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bd52-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bd52-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bd52-118">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0bd52-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0bd52-119">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0bd52-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd52-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bd52-120">Requirements</span></span>  
 <span data-ttu-id="0bd52-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd52-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd52-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bd52-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bd52-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bd52-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd52-124">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd52-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd52-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bd52-125">See also</span></span>
- [<span data-ttu-id="0bd52-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0bd52-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0bd52-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0bd52-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
