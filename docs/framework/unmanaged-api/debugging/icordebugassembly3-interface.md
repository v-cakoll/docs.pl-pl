---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eecb135e034c3565e805ea776115579488b2a4d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645464"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="7cbfe-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="7cbfe-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="7cbfe-103">Rozszerza logicznie icordebugassembly — interfejs w celu zapewnienia obsługi kontenerów zestawów i ich zestawy zawarte.</span><span class="sxs-lookup"><span data-stu-id="7cbfe-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7cbfe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7cbfe-104">Methods</span></span>  
  
|<span data-ttu-id="7cbfe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7cbfe-105">Method</span></span>|<span data-ttu-id="7cbfe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7cbfe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7cbfe-107">EnumerateContainedAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="7cbfe-107">EnumerateContainedAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="7cbfe-108">Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="7cbfe-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="7cbfe-109">GetContainerAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="7cbfe-109">GetContainerAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="7cbfe-110">Zwraca zestaw kontenerów to `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cbfe-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cbfe-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cbfe-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cbfe-112">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cbfe-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="7cbfe-113">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7cbfe-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cbfe-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cbfe-114">Requirements</span></span>  
 <span data-ttu-id="7cbfe-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cbfe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cbfe-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cbfe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cbfe-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cbfe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cbfe-118">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cbfe-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cbfe-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cbfe-119">See also</span></span>

- [<span data-ttu-id="7cbfe-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7cbfe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7cbfe-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7cbfe-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
