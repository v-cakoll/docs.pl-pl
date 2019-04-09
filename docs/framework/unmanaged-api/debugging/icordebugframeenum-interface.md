---
title: ICorDebugFrameEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd24dfa6771ca450e79b4b932735968ecc51fc90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093829"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="adfcd-102">ICorDebugFrameEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="adfcd-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="adfcd-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="adfcd-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adfcd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="adfcd-104">Methods</span></span>  
  
|<span data-ttu-id="adfcd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="adfcd-105">Method</span></span>|<span data-ttu-id="adfcd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="adfcd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adfcd-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="adfcd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="adfcd-108">Pobiera określoną liczbę `ICorDebugFrame` wystąpień z wyliczenia, zaczynając od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="adfcd-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adfcd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="adfcd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adfcd-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="adfcd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adfcd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="adfcd-111">Requirements</span></span>  
 <span data-ttu-id="adfcd-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adfcd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adfcd-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adfcd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adfcd-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adfcd-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="adfcd-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="adfcd-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="adfcd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="adfcd-116">See also</span></span>

- [<span data-ttu-id="adfcd-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="adfcd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
