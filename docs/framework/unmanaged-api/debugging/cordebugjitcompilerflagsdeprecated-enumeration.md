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
ms.openlocfilehash: 7b8a726cffcc00d7371675192a209b2d8e9db94d
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795784"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="5d437-102">CorDebugJITCompilerFlagsDeprecated — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5d437-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="5d437-103">To wyliczenie jest przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="5d437-103">This enumeration is obsolete.</span></span> <span data-ttu-id="5d437-104">Zamiast tego `CORDEBUG_JIT_DEFAULT` Użyj elementu członkowskiego wyliczenia [CorDebugJITCompilerFlags —](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5d437-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d437-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d437-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="5d437-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5d437-106">Members</span></span>  
  
|<span data-ttu-id="5d437-107">Członek</span><span class="sxs-lookup"><span data-stu-id="5d437-107">Member</span></span>|<span data-ttu-id="5d437-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5d437-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="5d437-109">Zamiast tego użyj polecenia cmdlet `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="5d437-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d437-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d437-110">Requirements</span></span>  
 <span data-ttu-id="5d437-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d437-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d437-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5d437-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d437-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d437-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d437-114">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5d437-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d437-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d437-115">See also</span></span>

- [<span data-ttu-id="5d437-116">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5d437-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
