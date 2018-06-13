---
title: Interfejs ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6ccd43059f33a69b8b052f9efa34c4e4f2c1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417719"
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="48317-102">Interfejs ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="48317-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="48317-103">Reprezentuje informacje symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="48317-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48317-104">Metody</span><span class="sxs-lookup"><span data-stu-id="48317-104">Methods</span></span>  
  
|<span data-ttu-id="48317-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="48317-105">Method</span></span>|<span data-ttu-id="48317-106">Opis</span><span class="sxs-lookup"><span data-stu-id="48317-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48317-107">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="48317-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="48317-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="48317-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="48317-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="48317-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="48317-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="48317-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="48317-111">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="48317-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="48317-112">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="48317-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48317-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48317-113">Remarks</span></span>  
 <span data-ttu-id="48317-114">`ICorDebugInstanceFieldSymbol` Interfejs służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="48317-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48317-115">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="48317-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="48317-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="48317-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48317-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48317-117">Requirements</span></span>  
 <span data-ttu-id="48317-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48317-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48317-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48317-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48317-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48317-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48317-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48317-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48317-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48317-122">See Also</span></span>  
 [<span data-ttu-id="48317-123">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="48317-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="48317-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="48317-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="48317-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="48317-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
