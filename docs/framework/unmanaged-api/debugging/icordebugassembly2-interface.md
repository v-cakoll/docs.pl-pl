---
title: ICorDebugAssembly2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: a0482ff451b05ec50c199a75a3c3fabd68c28e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133997"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="f0fcb-102">ICorDebugAssembly2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0fcb-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="f0fcb-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="f0fcb-103">Represents an assembly.</span></span> <span data-ttu-id="f0fcb-104">Ten interfejs jest rozszerzeniem interfejsu ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="f0fcb-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0fcb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f0fcb-105">Methods</span></span>  
  
|<span data-ttu-id="f0fcb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0fcb-106">Method</span></span>|<span data-ttu-id="f0fcb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f0fcb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0fcb-108">IsFullyTrusted, metoda</span><span class="sxs-lookup"><span data-stu-id="f0fcb-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="f0fcb-109">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f0fcb-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0fcb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0fcb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0fcb-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f0fcb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0fcb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0fcb-112">Requirements</span></span>  
 <span data-ttu-id="f0fcb-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0fcb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0fcb-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0fcb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0fcb-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f0fcb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0fcb-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0fcb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fcb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0fcb-117">See also</span></span>

- [<span data-ttu-id="f0fcb-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0fcb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
