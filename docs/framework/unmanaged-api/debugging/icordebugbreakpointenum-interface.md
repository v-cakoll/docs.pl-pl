---
title: ICorDebugBreakpointEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b5268eb4240f7c3ff254f4d3d9a13ab494530a1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968741"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="316f4-102">ICorDebugBreakpointEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="316f4-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="316f4-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="316f4-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="316f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="316f4-104">Methods</span></span>  
  
|<span data-ttu-id="316f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="316f4-105">Method</span></span>|<span data-ttu-id="316f4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="316f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="316f4-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="316f4-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="316f4-108">Pobiera określoną liczbę `ICorDebugBreakpoint` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="316f4-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="316f4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="316f4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="316f4-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="316f4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="316f4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="316f4-111">Requirements</span></span>  
 <span data-ttu-id="316f4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="316f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="316f4-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="316f4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="316f4-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="316f4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="316f4-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="316f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316f4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="316f4-116">See also</span></span>
- [<span data-ttu-id="316f4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="316f4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
