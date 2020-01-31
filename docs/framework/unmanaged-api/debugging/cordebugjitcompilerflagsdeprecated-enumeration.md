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
ms.openlocfilehash: 39b90ba35510a5eda7b34e0a80b0e889e5804ca7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778231"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="2b5b7-102">CorDebugJITCompilerFlagsDeprecated — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2b5b7-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="2b5b7-103">To wyliczenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="2b5b7-103">This enumeration is obsolete.</span></span> <span data-ttu-id="2b5b7-104">Zamiast tego użyj `CORDEBUG_JIT_DEFAULT` elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="2b5b7-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b5b7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b5b7-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="2b5b7-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2b5b7-106">Members</span></span>  
  
|<span data-ttu-id="2b5b7-107">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2b5b7-107">Member</span></span>|<span data-ttu-id="2b5b7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="2b5b7-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="2b5b7-109">Zamiast nich należy używać słów kluczowych `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="2b5b7-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b5b7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b5b7-110">Requirements</span></span>  
 <span data-ttu-id="2b5b7-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b5b7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b5b7-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2b5b7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b5b7-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2b5b7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b5b7-114">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2b5b7-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b5b7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b5b7-115">See also</span></span>

- [<span data-ttu-id="2b5b7-116">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2b5b7-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
