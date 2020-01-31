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
ms.openlocfilehash: 20e2e3f177b12221832786f4fab86635098d1989
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790492"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="4f2ee-102">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="4f2ee-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="4f2ee-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="4f2ee-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4f2ee-104">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="4f2ee-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2ee-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f2ee-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="4f2ee-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4f2ee-106">Members</span></span>  
  
|<span data-ttu-id="4f2ee-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="4f2ee-107">Member name</span></span>|<span data-ttu-id="4f2ee-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4f2ee-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="4f2ee-109">Debuger nie ma dostępu do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="4f2ee-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="4f2ee-110">Debuger ma dostęp do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="4f2ee-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f2ee-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f2ee-111">Remarks</span></span>  
 <span data-ttu-id="4f2ee-112">Element członkowski wyliczenia `ILCodeKind` można przesłać do metod [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) , aby określić, czy debuger może uzyskać dostęp do zmiennych dodanych w Instrumentacji ReJIT profilera, oraz do metody [GetCodeEx](icordebugilframe4-getcodeex-method.md) , aby określić, czy debuger może uzyskać dostęp do Instrumentacji Il.</span><span class="sxs-lookup"><span data-stu-id="4f2ee-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f2ee-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f2ee-113">Requirements</span></span>  
 <span data-ttu-id="4f2ee-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f2ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f2ee-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4f2ee-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f2ee-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f2ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f2ee-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f2ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f2ee-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f2ee-118">See also</span></span>

- [<span data-ttu-id="4f2ee-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4f2ee-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="4f2ee-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f2ee-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="4f2ee-121">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="4f2ee-121">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
