---
title: CorDebugJITCompilerFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 8be8ce36b557831bc0997dd1c69abb924390d051
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795826"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="1ca2e-102">CorDebugJITCompilerFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1ca2e-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="1ca2e-103">Zawiera wartości wpływające na zachowanie kompilatora zarządzanego (just-in-Time).</span><span class="sxs-lookup"><span data-stu-id="1ca2e-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ca2e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1ca2e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1ca2e-105">Members</span></span>  
  
|<span data-ttu-id="1ca2e-106">Członek</span><span class="sxs-lookup"><span data-stu-id="1ca2e-106">Member</span></span>|<span data-ttu-id="1ca2e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1ca2e-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="1ca2e-108">Określa, że kompilator ma śledzić dane kompilacji i umożliwia optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="1ca2e-109">Określa, że kompilator ma śledzić dane kompilacji, ale wyłącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="1ca2e-110">Określa, że kompilator ma śledzić dane kompilacji, wyłącza optymalizacje i umożliwia korzystanie z technologii Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="1ca2e-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ca2e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ca2e-111">Requirements</span></span>  
 <span data-ttu-id="1ca2e-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ca2e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ca2e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ca2e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ca2e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1ca2e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ca2e-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ca2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca2e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ca2e-116">See also</span></span>

- [<span data-ttu-id="1ca2e-117">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1ca2e-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
