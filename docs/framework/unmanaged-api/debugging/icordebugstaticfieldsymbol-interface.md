---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f4e245e96ac9d47db10072e50a5b3c516d5dd27
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962679"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="27872-102">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="27872-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="27872-103">Przedstawia informacje o symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="27872-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27872-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27872-104">Methods</span></span>  
  
|<span data-ttu-id="27872-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27872-105">Method</span></span>|<span data-ttu-id="27872-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27872-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27872-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="27872-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="27872-108">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="27872-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="27872-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="27872-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="27872-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="27872-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="27872-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="27872-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="27872-112">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="27872-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27872-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27872-113">Remarks</span></span>  
 <span data-ttu-id="27872-114">`ICorDebugStaticFieldSymbol` Interfejs jest używany do pobierania informacji o symbolach debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="27872-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27872-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27872-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="27872-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="27872-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27872-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27872-117">Requirements</span></span>  
 <span data-ttu-id="27872-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27872-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27872-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27872-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27872-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27872-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27872-121">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27872-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27872-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27872-122">See also</span></span>

- [<span data-ttu-id="27872-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="27872-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="27872-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="27872-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27872-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="27872-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
