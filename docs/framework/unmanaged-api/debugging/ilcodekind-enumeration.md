---
title: Wyliczenie ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: b59fbc2acefa907bb3f881b7ed183388d2e4c368
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103368"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="f86ed-102">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="f86ed-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="f86ed-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f86ed-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f86ed-104">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f86ed-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86ed-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f86ed-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="f86ed-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f86ed-106">Members</span></span>  
  
|<span data-ttu-id="f86ed-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="f86ed-107">Member name</span></span>|<span data-ttu-id="f86ed-108">Opis</span><span class="sxs-lookup"><span data-stu-id="f86ed-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="f86ed-109">Debuger nie ma dostępu do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f86ed-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="f86ed-110">Debuger ma dostęp do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="f86ed-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f86ed-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f86ed-111">Remarks</span></span>  
 <span data-ttu-id="f86ed-112">Element członkowski wyliczenia `ILCodeKind` można przesłać do metod [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) , aby określić, czy debuger może uzyskać dostęp do zmiennych dodanych w instrumentacji profilera ReJIT oraz do [GetCodeEx ](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)Metoda określająca, czy debuger może uzyskać dostęp do instrumentu Il.</span><span class="sxs-lookup"><span data-stu-id="f86ed-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f86ed-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f86ed-113">Requirements</span></span>  
 <span data-ttu-id="f86ed-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f86ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f86ed-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f86ed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f86ed-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f86ed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f86ed-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f86ed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f86ed-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f86ed-118">See also</span></span>

- [<span data-ttu-id="f86ed-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f86ed-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="f86ed-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="f86ed-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="f86ed-121">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="f86ed-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
