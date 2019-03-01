---
title: ICorDebugThreadEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b620357967d5d22148f64a3258fbb8dc52361d86
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981728"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="68be8-102">ICorDebugThreadEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="68be8-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="68be8-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="68be8-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68be8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="68be8-104">Methods</span></span>  
  
|<span data-ttu-id="68be8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="68be8-105">Method</span></span>|<span data-ttu-id="68be8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="68be8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68be8-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="68be8-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="68be8-108">Pobiera określoną liczbę `ICorDebugThread` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="68be8-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68be8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68be8-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68be8-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="68be8-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68be8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68be8-111">Requirements</span></span>  
 <span data-ttu-id="68be8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68be8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68be8-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68be8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68be8-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68be8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68be8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68be8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68be8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68be8-116">See also</span></span>
- [<span data-ttu-id="68be8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="68be8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
