---
title: ICorDebugValueEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: ba61df045caa117acae3756eb879cf67d0791222
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791068"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="29dd0-102">ICorDebugValueEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="29dd0-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="29dd0-103">Implementuje metody "ICorDebugEnum" i wylicza tablice "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="29dd0-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29dd0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29dd0-104">Methods</span></span>  
  
|<span data-ttu-id="29dd0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29dd0-105">Method</span></span>|<span data-ttu-id="29dd0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="29dd0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29dd0-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="29dd0-107">Next Method</span></span>](icordebugvalueenum-next-method.md)|<span data-ttu-id="29dd0-108">Pobiera określoną liczbę wystąpień `ICorDebugValue` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="29dd0-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29dd0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29dd0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29dd0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="29dd0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29dd0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29dd0-111">Requirements</span></span>  
 <span data-ttu-id="29dd0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dd0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dd0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29dd0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29dd0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29dd0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29dd0-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dd0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29dd0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29dd0-116">See also</span></span>

- [<span data-ttu-id="29dd0-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="29dd0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
