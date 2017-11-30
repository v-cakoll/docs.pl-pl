---
title: Interfejs ICorDebugInstanceFieldSymbol
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbf3f07f5669c4fcafa4d3cc4119fc715539651d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a><span data-ttu-id="76b8b-102">Interfejs ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="76b8b-102">ICorDebugInstanceFieldSymbol Interface</span></span>
<span data-ttu-id="76b8b-103">Reprezentuje informacje symbolu debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76b8b-103">Represents the debug symbol information for an instance field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76b8b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="76b8b-104">Methods</span></span>  
  
|<span data-ttu-id="76b8b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="76b8b-105">Method</span></span>|<span data-ttu-id="76b8b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="76b8b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76b8b-107">GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="76b8b-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|<span data-ttu-id="76b8b-108">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76b8b-108">Gets the name of the instance field.</span></span>|  
|[<span data-ttu-id="76b8b-109">GetOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="76b8b-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|<span data-ttu-id="76b8b-110">Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="76b8b-110">Gets the offset in bytes of this instance field in its parent class.</span></span>|  
|[<span data-ttu-id="76b8b-111">GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="76b8b-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|<span data-ttu-id="76b8b-112">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76b8b-112">Gets the size in bytes of the instance field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76b8b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76b8b-113">Remarks</span></span>  
 <span data-ttu-id="76b8b-114">`ICorDebugInstanceFieldSymbol` Interfejs służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="76b8b-114">The `ICorDebugInstanceFieldSymbol` interface is used to retrieve the debug symbol information for an instance field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76b8b-115">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="76b8b-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="76b8b-116">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="76b8b-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76b8b-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76b8b-117">Requirements</span></span>  
 <span data-ttu-id="76b8b-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76b8b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76b8b-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="76b8b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76b8b-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76b8b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76b8b-121">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76b8b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76b8b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76b8b-122">See Also</span></span>  
 [<span data-ttu-id="76b8b-123">Interfejs ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="76b8b-123">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="76b8b-124">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="76b8b-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="76b8b-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="76b8b-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
