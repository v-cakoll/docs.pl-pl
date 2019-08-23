---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e5f63df9354df6a4d142c2f6ae12f9a0d5600fb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910141"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="e7a8b-102">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7a8b-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="e7a8b-103">Przedstawia informacje o symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7a8b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7a8b-104">Methods</span></span>  
  
|<span data-ttu-id="e7a8b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7a8b-105">Method</span></span>|<span data-ttu-id="e7a8b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e7a8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7a8b-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="e7a8b-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="e7a8b-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="e7a8b-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="e7a8b-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="e7a8b-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="e7a8b-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="e7a8b-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="e7a8b-112">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7a8b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7a8b-113">Remarks</span></span>  
 <span data-ttu-id="e7a8b-114">`ICorDebugInstanceFieldSymbol` Interfejs jest używany do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7a8b-115">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="e7a8b-116">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="e7a8b-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a8b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e7a8b-117">Requirements</span></span>  
 <span data-ttu-id="e7a8b-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a8b-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7a8b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7a8b-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7a8b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a8b-121">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a8b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a8b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7a8b-122">See also</span></span>

- [<span data-ttu-id="e7a8b-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e7a8b-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e7a8b-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e7a8b-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e7a8b-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e7a8b-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
