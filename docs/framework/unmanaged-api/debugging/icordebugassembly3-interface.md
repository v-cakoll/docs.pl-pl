---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca77360c36ff2cdce7ee47d5c3883dd824c6cef8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959327"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="bf689-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="bf689-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="bf689-103">Logicznie rozszerza interfejs ICorDebugAssembly w celu zapewnienia obsługi zestawów kontenerów i zawartych w nich zestawów.</span><span class="sxs-lookup"><span data-stu-id="bf689-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf689-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bf689-104">Methods</span></span>  
  
|<span data-ttu-id="bf689-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf689-105">Method</span></span>|<span data-ttu-id="bf689-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bf689-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf689-107">EnumerateContainedAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="bf689-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="bf689-108">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="bf689-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="bf689-109">GetContainerAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="bf689-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="bf689-110">Zwraca zestaw kontenerów tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bf689-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf689-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf689-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf689-112">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bf689-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bf689-113">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bf689-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf689-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf689-114">Requirements</span></span>  
 <span data-ttu-id="bf689-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf689-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf689-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf689-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf689-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf689-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf689-118">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf689-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf689-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf689-119">See also</span></span>

- [<span data-ttu-id="bf689-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf689-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bf689-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bf689-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
