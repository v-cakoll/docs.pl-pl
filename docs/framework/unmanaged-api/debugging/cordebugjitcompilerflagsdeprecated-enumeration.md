---
title: CorDebugJITCompilerFlagsDeprecated — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: d731b12ddf195137ff38d32ab0ca52aa90f48d4e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132786"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="67245-102">CorDebugJITCompilerFlagsDeprecated — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="67245-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="67245-103">To wyliczenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="67245-103">This enumeration is obsolete.</span></span> <span data-ttu-id="67245-104">Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="67245-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67245-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="67245-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="67245-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="67245-106">Members</span></span>  
  
|<span data-ttu-id="67245-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="67245-107">Member</span></span>|<span data-ttu-id="67245-108">Opis</span><span class="sxs-lookup"><span data-stu-id="67245-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="67245-109">Zamiast nich należy używać słów kluczowych `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="67245-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67245-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="67245-110">Requirements</span></span>  
 <span data-ttu-id="67245-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67245-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67245-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="67245-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67245-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="67245-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67245-114">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="67245-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67245-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67245-115">See also</span></span>

- [<span data-ttu-id="67245-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="67245-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
