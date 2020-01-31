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
ms.openlocfilehash: 7f1c5d7a6fdae3e4c5a66c9aa4a82911105f4597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788505"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="5ded5-102">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="5ded5-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="5ded5-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="5ded5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5ded5-104">Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="5ded5-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="5ded5-105">Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="5ded5-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5ded5-106">Metody</span><span class="sxs-lookup"><span data-stu-id="5ded5-106">Methods</span></span>  
  
|<span data-ttu-id="5ded5-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="5ded5-107">Method</span></span>|<span data-ttu-id="5ded5-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5ded5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5ded5-109">EnumerateLocalVariablesEx, metoda</span><span class="sxs-lookup"><span data-stu-id="5ded5-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="5ded5-110">Zwraca listę zmiennych lokalnych dostępnych w bieżącej klatce.</span><span class="sxs-lookup"><span data-stu-id="5ded5-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="5ded5-111">GetCodeEx, metoda</span><span class="sxs-lookup"><span data-stu-id="5ded5-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="5ded5-112">Zwraca kod, w którym jest uruchomiona ta ramka stosu.</span><span class="sxs-lookup"><span data-stu-id="5ded5-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="5ded5-113">GetLocalVariableEx, metoda</span><span class="sxs-lookup"><span data-stu-id="5ded5-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="5ded5-114">Zwraca wartość zmiennej lokalnej w ramce IL.</span><span class="sxs-lookup"><span data-stu-id="5ded5-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ded5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ded5-115">Remarks</span></span>  
 <span data-ttu-id="5ded5-116">Te metody oferują funkcje oprócz tych zapewnianych przez metody [EnumerateLocalVariables —](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)i [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5ded5-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="5ded5-117">Każda metoda zawiera parametr `flags`, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowane przez żądanie ReJIT profilera.</span><span class="sxs-lookup"><span data-stu-id="5ded5-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ded5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5ded5-118">Requirements</span></span>  
 <span data-ttu-id="5ded5-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ded5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ded5-120">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5ded5-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ded5-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5ded5-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ded5-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ded5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ded5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ded5-123">See also</span></span>

- [<span data-ttu-id="5ded5-124">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5ded5-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5ded5-125">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5ded5-125">Debugging</span></span>](index.md)
