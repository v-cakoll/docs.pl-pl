---
title: ICorDebugInternalFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a1af92cbce84b674058ab2c8af2e15b0070dcd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974760"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="8738e-102">ICorDebugInternalFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8738e-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="8738e-103">Reprezentuje ramkę wewnętrznego środowiska uruchomieniowego na stosie.</span><span class="sxs-lookup"><span data-stu-id="8738e-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="8738e-104">Ten interfejs jest podklasą icordebugframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="8738e-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8738e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8738e-105">Methods</span></span>  
  
|<span data-ttu-id="8738e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8738e-106">Method</span></span>|<span data-ttu-id="8738e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8738e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8738e-108">GetFrameType, metoda</span><span class="sxs-lookup"><span data-stu-id="8738e-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="8738e-109">Pobiera typ tej ramki wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="8738e-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8738e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8738e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8738e-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="8738e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8738e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8738e-112">Requirements</span></span>  
 <span data-ttu-id="8738e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8738e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8738e-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8738e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8738e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8738e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8738e-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8738e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8738e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8738e-117">See also</span></span>
- [<span data-ttu-id="8738e-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8738e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
