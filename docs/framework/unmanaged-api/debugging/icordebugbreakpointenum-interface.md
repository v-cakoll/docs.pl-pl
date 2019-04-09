---
title: ICorDebugBreakpointEnum, interfejs
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
ms.openlocfilehash: 7fd42f13f699b0b79fd69311186f2b2ca0c9998a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149074"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="fa885-102">ICorDebugBreakpointEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="fa885-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="fa885-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="fa885-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fa885-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fa885-104">Methods</span></span>  
  
|<span data-ttu-id="fa885-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fa885-105">Method</span></span>|<span data-ttu-id="fa885-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fa885-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fa885-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="fa885-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="fa885-108">Pobiera określoną liczbę `ICorDebugBreakpoint` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="fa885-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa885-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa885-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa885-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="fa885-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa885-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fa885-111">Requirements</span></span>  
 <span data-ttu-id="fa885-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa885-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa885-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa885-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa885-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa885-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fa885-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fa885-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fa885-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa885-116">See also</span></span>

- [<span data-ttu-id="fa885-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="fa885-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
