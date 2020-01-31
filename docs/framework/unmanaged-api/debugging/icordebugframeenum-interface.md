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
ms.openlocfilehash: 6cc1ef5f778902efaa53156fbefe334046c82114
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794539"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="2d9bc-102">ICorDebugFrameEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d9bc-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="2d9bc-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2d9bc-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2d9bc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2d9bc-104">Methods</span></span>  
  
|<span data-ttu-id="2d9bc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2d9bc-105">Method</span></span>|<span data-ttu-id="2d9bc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2d9bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2d9bc-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="2d9bc-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="2d9bc-108">Pobiera określoną liczbę wystąpień `ICorDebugFrame` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="2d9bc-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d9bc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d9bc-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d9bc-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2d9bc-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d9bc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d9bc-111">Requirements</span></span>  
 <span data-ttu-id="2d9bc-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d9bc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d9bc-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d9bc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d9bc-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d9bc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d9bc-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d9bc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9bc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d9bc-116">See also</span></span>

- [<span data-ttu-id="2d9bc-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d9bc-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
