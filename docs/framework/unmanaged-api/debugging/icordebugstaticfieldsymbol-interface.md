---
title: Interfejs ICorDebugStaticFieldSymbol
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cde5f60764772ece8528eb67a82836c0ae9e651b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="97124-102">Interfejs ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="97124-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="97124-103">Reprezentuje informacje symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="97124-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97124-104">Metody</span><span class="sxs-lookup"><span data-stu-id="97124-104">Methods</span></span>  
  
|<span data-ttu-id="97124-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="97124-105">Method</span></span>|<span data-ttu-id="97124-106">Opis</span><span class="sxs-lookup"><span data-stu-id="97124-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97124-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="97124-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="97124-108">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="97124-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="97124-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="97124-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="97124-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="97124-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="97124-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="97124-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="97124-112">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="97124-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97124-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97124-113">Remarks</span></span>  
 <span data-ttu-id="97124-114">`ICorDebugStaticFieldSymbol` Interfejs służy do pobierania informacji o symbolach debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="97124-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97124-115">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="97124-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="97124-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="97124-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97124-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97124-117">Requirements</span></span>  
 <span data-ttu-id="97124-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97124-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97124-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97124-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97124-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97124-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97124-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97124-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97124-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97124-122">See Also</span></span>  
 [<span data-ttu-id="97124-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="97124-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="97124-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="97124-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="97124-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="97124-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
