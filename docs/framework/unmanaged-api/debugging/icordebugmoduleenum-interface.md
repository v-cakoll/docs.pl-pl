---
title: ICorDebugModuleEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf3d72b2439250fd8fbdc1bf1dc9ca28352c9ad
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976840"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="7e00f-102">ICorDebugModuleEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e00f-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="7e00f-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="7e00f-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e00f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e00f-104">Methods</span></span>  
  
|<span data-ttu-id="7e00f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e00f-105">Method</span></span>|<span data-ttu-id="7e00f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7e00f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e00f-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="7e00f-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="7e00f-108">Pobiera określoną liczbę `ICorDebugModule` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="7e00f-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e00f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e00f-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e00f-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="7e00f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e00f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e00f-111">Requirements</span></span>  
 <span data-ttu-id="7e00f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e00f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e00f-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e00f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e00f-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e00f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e00f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e00f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e00f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e00f-116">See also</span></span>
- [<span data-ttu-id="7e00f-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7e00f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
