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
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130852"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="cc6a9-102">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="cc6a9-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="cc6a9-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="cc6a9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="cc6a9-104">Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="cc6a9-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="cc6a9-105">Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="cc6a9-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cc6a9-106">Metody</span><span class="sxs-lookup"><span data-stu-id="cc6a9-106">Methods</span></span>  
  
|<span data-ttu-id="cc6a9-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="cc6a9-107">Method</span></span>|<span data-ttu-id="cc6a9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cc6a9-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cc6a9-109">EnumerateLocalVariablesEx, metoda</span><span class="sxs-lookup"><span data-stu-id="cc6a9-109">EnumerateLocalVariablesEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="cc6a9-110">Zwraca listę zmiennych lokalnych dostępnych w bieżącej klatce.</span><span class="sxs-lookup"><span data-stu-id="cc6a9-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="cc6a9-111">GetCodeEx, metoda</span><span class="sxs-lookup"><span data-stu-id="cc6a9-111">GetCodeEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="cc6a9-112">Zwraca kod, w którym jest uruchomiona ta ramka stosu.</span><span class="sxs-lookup"><span data-stu-id="cc6a9-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="cc6a9-113">GetLocalVariableEx, metoda</span><span class="sxs-lookup"><span data-stu-id="cc6a9-113">GetLocalVariableEx Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="cc6a9-114">Zwraca wartość zmiennej lokalnej w ramce IL.</span><span class="sxs-lookup"><span data-stu-id="cc6a9-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc6a9-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc6a9-115">Remarks</span></span>  
 <span data-ttu-id="cc6a9-116">Te metody oferują funkcje oprócz tych zapewnianych przez metody [EnumerateLocalVariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)i [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cc6a9-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), and [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="cc6a9-117">Każda metoda zawiera parametr `flags`, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowane przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="cc6a9-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc6a9-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc6a9-118">Requirements</span></span>  
 <span data-ttu-id="cc6a9-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc6a9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc6a9-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cc6a9-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc6a9-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cc6a9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc6a9-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc6a9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc6a9-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc6a9-123">See also</span></span>

- [<span data-ttu-id="cc6a9-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cc6a9-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cc6a9-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cc6a9-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
