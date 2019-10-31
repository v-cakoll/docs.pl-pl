---
title: ICorDebugStaticFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: 0891df1fc0528ff485605b2c4168fcff0adff990
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131703"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="1423c-102">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="1423c-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="1423c-103">Przedstawia informacje o symbolu debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1423c-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1423c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1423c-104">Methods</span></span>  
  
|<span data-ttu-id="1423c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1423c-105">Method</span></span>|<span data-ttu-id="1423c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1423c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1423c-107">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="1423c-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="1423c-108">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1423c-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="1423c-109">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="1423c-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="1423c-110">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1423c-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="1423c-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="1423c-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="1423c-112">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1423c-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1423c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1423c-113">Remarks</span></span>  
 <span data-ttu-id="1423c-114">Interfejs `ICorDebugStaticFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="1423c-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1423c-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1423c-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1423c-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="1423c-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1423c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1423c-117">Requirements</span></span>  
 <span data-ttu-id="1423c-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1423c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1423c-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1423c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1423c-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1423c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1423c-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1423c-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1423c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1423c-122">See also</span></span>

- [<span data-ttu-id="1423c-123">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="1423c-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="1423c-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1423c-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1423c-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1423c-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
