---
title: ICorDebugAssembly2, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b42cb2bff677963c44bfc04f8bdd6c60497e4731
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909887"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="21698-102">ICorDebugAssembly2, interfejs</span><span class="sxs-lookup"><span data-stu-id="21698-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="21698-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="21698-103">Represents an assembly.</span></span> <span data-ttu-id="21698-104">Ten interfejs jest rozszerzeniem interfejsu ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="21698-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21698-105">Metody</span><span class="sxs-lookup"><span data-stu-id="21698-105">Methods</span></span>  
  
|<span data-ttu-id="21698-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="21698-106">Method</span></span>|<span data-ttu-id="21698-107">Opis</span><span class="sxs-lookup"><span data-stu-id="21698-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21698-108">IsFullyTrusted, metoda</span><span class="sxs-lookup"><span data-stu-id="21698-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="21698-109">Pobiera wartość wskazującą, czy zestaw ma przyznane pełne zaufanie przez system zabezpieczeń środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="21698-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21698-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21698-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21698-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="21698-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21698-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21698-112">Requirements</span></span>  
 <span data-ttu-id="21698-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21698-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21698-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21698-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21698-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21698-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21698-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21698-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21698-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21698-117">See also</span></span>

- [<span data-ttu-id="21698-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="21698-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
