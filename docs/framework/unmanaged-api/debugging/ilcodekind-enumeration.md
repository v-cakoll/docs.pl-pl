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
ms.openlocfilehash: 0586b9e184a0958b978837601db002e035881cbc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421036"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="5d96c-102">Wyliczenie ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="5d96c-102">ILCodeKind Enumeration</span></span>
<span data-ttu-id="5d96c-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="5d96c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5d96c-104">Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5d96c-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d96c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d96c-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="5d96c-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d96c-106">Members</span></span>  
  
|<span data-ttu-id="5d96c-107">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="5d96c-107">Member name</span></span>|<span data-ttu-id="5d96c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5d96c-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="5d96c-109">Debuger nie ma dostępu do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5d96c-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="5d96c-110">Debuger ma dostęp do informacji z Instrumentacji ReJIT.</span><span class="sxs-lookup"><span data-stu-id="5d96c-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d96c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d96c-111">Remarks</span></span>  
 <span data-ttu-id="5d96c-112">Element członkowski `ILCodeKind` wyliczenia można przesłać do metod [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) , aby określić, czy debuger może uzyskać dostęp do zmiennych dodanych w Instrumentacji ReJIT profilera, oraz do metody [GetCodeEx](icordebugilframe4-getcodeex-method.md) , aby określić, czy debuger może uzyskać dostęp do instrumentu Il.</span><span class="sxs-lookup"><span data-stu-id="5d96c-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d96c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d96c-113">Requirements</span></span>  
 <span data-ttu-id="5d96c-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d96c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d96c-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d96c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d96c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d96c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d96c-117">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d96c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d96c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d96c-118">See also</span></span>

- [<span data-ttu-id="5d96c-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5d96c-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="5d96c-120">Interfejs ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="5d96c-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="5d96c-121">ReJIT: Przewodnik po poradniku</span><span class="sxs-lookup"><span data-stu-id="5d96c-121">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
