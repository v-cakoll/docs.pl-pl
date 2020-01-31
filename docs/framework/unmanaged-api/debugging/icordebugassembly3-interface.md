---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: deb300ced2ff7a116bd443c9a7b10dcc0b7955ac
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784533"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="594ec-102">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="594ec-102">ICorDebugAssembly3 Interface</span></span>
<span data-ttu-id="594ec-103">Logicznie rozszerza interfejs ICorDebugAssembly w celu zapewnienia obsługi zestawów kontenerów i zawartych w nich zestawów.</span><span class="sxs-lookup"><span data-stu-id="594ec-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="594ec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="594ec-104">Methods</span></span>  
  
|<span data-ttu-id="594ec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="594ec-105">Method</span></span>|<span data-ttu-id="594ec-106">Opis</span><span class="sxs-lookup"><span data-stu-id="594ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="594ec-107">EnumerateContainedAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="594ec-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="594ec-108">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="594ec-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="594ec-109">GetContainerAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="594ec-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="594ec-110">Zwraca zestaw kontenerów tego obiektu `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="594ec-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="594ec-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="594ec-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="594ec-112">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="594ec-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="594ec-113">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="594ec-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="594ec-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="594ec-114">Requirements</span></span>  
 <span data-ttu-id="594ec-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="594ec-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="594ec-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="594ec-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="594ec-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="594ec-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="594ec-118">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="594ec-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594ec-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="594ec-119">See also</span></span>

- [<span data-ttu-id="594ec-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="594ec-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="594ec-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="594ec-121">Debugging</span></span>](index.md)
