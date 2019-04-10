---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eecb135e034c3565e805ea776115579488b2a4d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210311"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="30058-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="30058-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="30058-103">Rozszerza logicznie icordebugassembly — interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte.</span><span class="sxs-lookup"><span data-stu-id="30058-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30058-104">Metody</span><span class="sxs-lookup"><span data-stu-id="30058-104">Methods</span></span>  
  
|<span data-ttu-id="30058-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="30058-105">Method</span></span>|<span data-ttu-id="30058-106">Opis</span><span class="sxs-lookup"><span data-stu-id="30058-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30058-107">EnumerateContainedAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="30058-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="30058-108">Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="30058-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="30058-109">GetContainerAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="30058-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="30058-110">Zwraca zestaw kontenerów to `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="30058-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30058-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30058-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30058-112">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30058-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="30058-113">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30058-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30058-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30058-114">Requirements</span></span>  
 <span data-ttu-id="30058-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30058-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30058-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30058-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30058-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30058-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="30058-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="30058-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="30058-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30058-119">See also</span></span>

- [<span data-ttu-id="30058-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="30058-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="30058-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="30058-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
