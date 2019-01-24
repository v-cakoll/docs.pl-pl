---
title: Interfejs ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb3f55a8a0ddff6c3202d15dc4704d443cabb44d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656950"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="9331d-102">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="9331d-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="9331d-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="9331d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9331d-104">Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="9331d-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="9331d-105">Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="9331d-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9331d-106">Metody</span><span class="sxs-lookup"><span data-stu-id="9331d-106">Methods</span></span>  
  
|<span data-ttu-id="9331d-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="9331d-107">Method</span></span>|<span data-ttu-id="9331d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9331d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9331d-109">EnumerateLocalVariablesEx, metoda</span><span class="sxs-lookup"><span data-stu-id="9331d-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="9331d-110">Zwraca listę zmiennych lokalnych dostępnych w bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="9331d-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="9331d-111">GetCodeEx, metoda</span><span class="sxs-lookup"><span data-stu-id="9331d-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="9331d-112">Zwraca kod, który działa tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="9331d-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="9331d-113">GetLocalVariableEx, metoda</span><span class="sxs-lookup"><span data-stu-id="9331d-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="9331d-114">Zwraca wartość zmiennej lokalnej w ramce IL.</span><span class="sxs-lookup"><span data-stu-id="9331d-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9331d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9331d-115">Remarks</span></span>  
 <span data-ttu-id="9331d-116">Te metody oferują funkcje oprócz tego są udostępniane przez [enumeratelocalvariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode —](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), i [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9331d-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="9331d-117">Każda metoda obejmuje `flags` parametr, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowany przez profiler ReJIT żądanie.</span><span class="sxs-lookup"><span data-stu-id="9331d-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9331d-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9331d-118">Requirements</span></span>  
 <span data-ttu-id="9331d-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9331d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9331d-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9331d-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9331d-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9331d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9331d-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9331d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9331d-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9331d-123">See also</span></span>
- [<span data-ttu-id="9331d-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9331d-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9331d-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9331d-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
