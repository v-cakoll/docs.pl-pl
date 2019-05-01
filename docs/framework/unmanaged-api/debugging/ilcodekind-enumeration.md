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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f7e20618180961ab6d8ad0bbb79a626a4a7f4f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993485"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="37da4-102">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="37da4-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="37da4-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="37da4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="37da4-104">Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w profilerze ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="37da4-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37da4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37da4-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="37da4-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="37da4-106">Members</span></span>  
  
|<span data-ttu-id="37da4-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="37da4-107">Member name</span></span>|<span data-ttu-id="37da4-108">Opis</span><span class="sxs-lookup"><span data-stu-id="37da4-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="37da4-109">Debuger nie ma dostępu do informacji z ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="37da4-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="37da4-110">Debuger ma dostęp do informacji z ReJIT instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="37da4-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37da4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37da4-111">Remarks</span></span>  
 <span data-ttu-id="37da4-112">Członek `ILCodeKind` wyliczenia mogą być przekazywane do [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metod umożliwiających ustalenie, czy debuger może uzyskać dostęp do zmiennych dodane w programie profiler Instrumentacja ReJIT i [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) metodę pozwala ustalić, czy debuger może uzyskiwać dostęp do Instrumentacji IL.</span><span class="sxs-lookup"><span data-stu-id="37da4-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37da4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37da4-113">Requirements</span></span>  
 <span data-ttu-id="37da4-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37da4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37da4-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37da4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37da4-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37da4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37da4-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37da4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37da4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37da4-118">See also</span></span>

- [<span data-ttu-id="37da4-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="37da4-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="37da4-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="37da4-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="37da4-121">ReJIT: Przewodniku z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="37da4-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
