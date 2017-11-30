---
title: Interfejs ICorDebugAssembly3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9ed476746e627be987e6307bd367f0d16374de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="56409-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="56409-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="56409-103">Logicznie rozszerza interfejs ICorDebugAssembly, aby zapewnić obsługę dla zestawów kontenera i ich zawartych w niej zestawów.</span><span class="sxs-lookup"><span data-stu-id="56409-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56409-104">Metody</span><span class="sxs-lookup"><span data-stu-id="56409-104">Methods</span></span>  
  
|<span data-ttu-id="56409-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="56409-105">Method</span></span>|<span data-ttu-id="56409-106">Opis</span><span class="sxs-lookup"><span data-stu-id="56409-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56409-107">Metoda EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="56409-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="56409-108">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="56409-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="56409-109">Metoda GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="56409-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="56409-110">Zwraca zestaw kontenera tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="56409-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56409-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56409-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="56409-112">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="56409-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="56409-113">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="56409-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56409-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56409-114">Requirements</span></span>  
 <span data-ttu-id="56409-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56409-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56409-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56409-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56409-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56409-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56409-118">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56409-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56409-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56409-119">See Also</span></span>  
 [<span data-ttu-id="56409-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="56409-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="56409-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="56409-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
