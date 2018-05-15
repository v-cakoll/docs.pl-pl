---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5042f59b3716d077cc441585004e075b765c0cfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="cddc9-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="cddc9-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="cddc9-103">Logicznie rozszerza interfejs ICorDebugAssembly, aby zapewnić obsługę dla zestawów kontenera i ich zawartych w niej zestawów.</span><span class="sxs-lookup"><span data-stu-id="cddc9-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cddc9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cddc9-104">Methods</span></span>  
  
|<span data-ttu-id="cddc9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cddc9-105">Method</span></span>|<span data-ttu-id="cddc9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cddc9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cddc9-107">EnumerateContainedAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="cddc9-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="cddc9-108">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="cddc9-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="cddc9-109">GetContainerAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="cddc9-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="cddc9-110">Zwraca zestaw kontenera tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="cddc9-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cddc9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cddc9-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cddc9-112">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cddc9-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="cddc9-113">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cddc9-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cddc9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cddc9-114">Requirements</span></span>  
 <span data-ttu-id="cddc9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cddc9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cddc9-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cddc9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cddc9-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cddc9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cddc9-118">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cddc9-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cddc9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cddc9-119">See Also</span></span>  
 [<span data-ttu-id="cddc9-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cddc9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cddc9-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cddc9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
