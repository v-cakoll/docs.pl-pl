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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 66a8ba59d221bb3fa2e815a1cbcfa79c474666cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105472"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="1a364-102">CorDebugJITCompilerFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1a364-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="1a364-103">Zawiera wartości, które wpływają na zachowanie zarządzanych kompilator just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="1a364-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a364-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a364-104">Syntax</span></span>  
  
```  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1a364-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1a364-105">Members</span></span>  
  
|<span data-ttu-id="1a364-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1a364-106">Member</span></span>|<span data-ttu-id="1a364-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1a364-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="1a364-108">Określa, że kompilator powinien śledzić dane kompilacji i umożliwia optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="1a364-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="1a364-109">Określa, czy kompilator powinien śledzić dane kompilacji, ale wyłącza optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="1a364-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="1a364-110">Określa się, że kompilator powinien śledzić dane kompilacji, wyłącza optymalizacje, i włącza tryb Edytuj i Kontynuuj technologii.</span><span class="sxs-lookup"><span data-stu-id="1a364-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a364-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a364-111">Requirements</span></span>  
 <span data-ttu-id="1a364-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a364-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a364-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a364-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a364-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a364-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a364-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a364-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a364-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a364-116">See also</span></span>

- [<span data-ttu-id="1a364-117">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1a364-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
