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
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206619"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="44349-102">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="44349-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="44349-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="44349-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="44349-104">Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="44349-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="44349-105">Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="44349-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44349-106">Metody</span><span class="sxs-lookup"><span data-stu-id="44349-106">Methods</span></span>  
  
|<span data-ttu-id="44349-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="44349-107">Method</span></span>|<span data-ttu-id="44349-108">Opis</span><span class="sxs-lookup"><span data-stu-id="44349-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44349-109">EnumerateLocalVariablesEx, metoda</span><span class="sxs-lookup"><span data-stu-id="44349-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="44349-110">Zwraca listę zmiennych lokalnych dostępnych w bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="44349-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="44349-111">GetCodeEx, metoda</span><span class="sxs-lookup"><span data-stu-id="44349-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="44349-112">Zwraca kod, który działa tej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="44349-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="44349-113">GetLocalVariableEx, metoda</span><span class="sxs-lookup"><span data-stu-id="44349-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="44349-114">Zwraca wartość zmiennej lokalnej w ramce IL.</span><span class="sxs-lookup"><span data-stu-id="44349-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44349-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44349-115">Remarks</span></span>  
 <span data-ttu-id="44349-116">Te metody oferują funkcje oprócz tego są udostępniane przez [enumeratelocalvariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode —](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), i [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="44349-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="44349-117">Każda metoda obejmuje `flags` parametr, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowany przez profiler ReJIT żądanie.</span><span class="sxs-lookup"><span data-stu-id="44349-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44349-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44349-118">Requirements</span></span>  
 <span data-ttu-id="44349-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44349-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44349-120">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44349-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44349-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44349-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44349-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44349-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44349-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44349-123">See also</span></span>

- [<span data-ttu-id="44349-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="44349-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="44349-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="44349-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
