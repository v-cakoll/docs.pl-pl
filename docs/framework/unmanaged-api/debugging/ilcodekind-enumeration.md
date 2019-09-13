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
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928813"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="d6c7d-102">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="d6c7d-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="d6c7d-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d6c7d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d6c7d-104">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d6c7d-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c7d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6c7d-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="d6c7d-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d6c7d-106">Members</span></span>  
  
|<span data-ttu-id="d6c7d-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="d6c7d-107">Member name</span></span>|<span data-ttu-id="d6c7d-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d6c7d-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="d6c7d-109">Debuger nie ma dostępu do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d6c7d-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="d6c7d-110">Debuger ma dostęp do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="d6c7d-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6c7d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6c7d-111">Remarks</span></span>  
 <span data-ttu-id="d6c7d-112">Element członkowski `ILCodeKind` wyliczenia można przesłać do [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metod, aby określić, czy debuger może uzyskać dostęp do zmiennych dodanych w instrumentacji profilera ReJIT oraz do [ GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) metodę, aby określić, czy debuger może uzyskać dostęp do instrumentu Il.</span><span class="sxs-lookup"><span data-stu-id="d6c7d-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c7d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6c7d-113">Requirements</span></span>  
 <span data-ttu-id="d6c7d-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6c7d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c7d-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6c7d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6c7d-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c7d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c7d-117">**.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c7d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c7d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6c7d-118">See also</span></span>

- [<span data-ttu-id="d6c7d-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="d6c7d-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="d6c7d-120">ICorDebugILFrame4, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6c7d-120">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [<span data-ttu-id="d6c7d-121">ReJIT: Przewodnik krok po kroku</span><span class="sxs-lookup"><span data-stu-id="d6c7d-121">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
