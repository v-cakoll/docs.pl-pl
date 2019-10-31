---
title: Interfejs ICorDebugDataTarget2
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 3c59752949ca29cbd0ed5a34ec7aeb3d98b6f9b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136484"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="0f599-102">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="0f599-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="0f599-103">Logicznie rozszerza interfejs [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0f599-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0f599-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0f599-104">Methods</span></span>  
  
|<span data-ttu-id="0f599-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-105">Method</span></span>|<span data-ttu-id="0f599-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0f599-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0f599-107">CreateVirtualUnwinder, metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="0f599-108">Tworzy nowy wątek unwiatrer, który zaczyna odwracać od kontekstu początkowego (co nie musi być elementem liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="0f599-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="0f599-109">EnumerateThreadIDs, metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="0f599-110">Zwraca listę aktywnych identyfikatorów wątków.</span><span class="sxs-lookup"><span data-stu-id="0f599-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="0f599-111">GetImageFromPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="0f599-112">Zwraca adres podstawowy i rozmiar modułu z adresu w tym module.</span><span class="sxs-lookup"><span data-stu-id="0f599-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="0f599-113">GetImageLocation, metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="0f599-114">Zwraca ścieżkę modułu z adresu podstawowego modułu.</span><span class="sxs-lookup"><span data-stu-id="0f599-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="0f599-115">GetSymbolProviderForImage, metoda</span><span class="sxs-lookup"><span data-stu-id="0f599-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="0f599-116">Zwraca dostawcę symboli dla modułu z adresu podstawowego tego modułu.</span><span class="sxs-lookup"><span data-stu-id="0f599-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f599-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f599-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f599-118">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0f599-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0f599-119">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0f599-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f599-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f599-120">Requirements</span></span>  
 <span data-ttu-id="0f599-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f599-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f599-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f599-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f599-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0f599-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f599-124">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f599-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f599-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f599-125">See also</span></span>

- [<span data-ttu-id="0f599-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0f599-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0f599-127">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0f599-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
