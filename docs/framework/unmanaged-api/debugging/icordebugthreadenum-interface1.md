---
title: ICorDebugThreadEnum, interfejs
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
ms.openlocfilehash: 7edf103e397c6e3e1577b5ed4bc8fc0df264b843
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137998"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="3662e-102">ICorDebugThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="3662e-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="3662e-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3662e-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3662e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3662e-104">Methods</span></span>  
  
|<span data-ttu-id="3662e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3662e-105">Method</span></span>|<span data-ttu-id="3662e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3662e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3662e-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="3662e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="3662e-108">Pobiera określoną liczbę `ICorDebugThread` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="3662e-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3662e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3662e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3662e-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="3662e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3662e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3662e-111">Requirements</span></span>  
 <span data-ttu-id="3662e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3662e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3662e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3662e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3662e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3662e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3662e-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3662e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3662e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3662e-116">See also</span></span>

- [<span data-ttu-id="3662e-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3662e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
