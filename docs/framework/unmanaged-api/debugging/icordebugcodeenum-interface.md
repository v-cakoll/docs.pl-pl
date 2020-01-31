---
title: ICorDebugCodeEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: 127022fb8e9f9559ccb0f0c877d25db67eea3037
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784015"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="63181-102">ICorDebugCodeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="63181-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="63181-103">Implementuje metody "ICorDebugEnum" i wylicza tablice "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="63181-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63181-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63181-104">Methods</span></span>  
  
|<span data-ttu-id="63181-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63181-105">Method</span></span>|<span data-ttu-id="63181-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63181-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63181-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="63181-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="63181-108">Pobiera określoną liczbę wystąpień `ICorDebugCode` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="63181-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63181-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63181-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63181-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="63181-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63181-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63181-111">Requirements</span></span>  
 <span data-ttu-id="63181-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63181-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63181-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="63181-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63181-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="63181-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63181-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63181-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63181-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63181-116">See also</span></span>

- [<span data-ttu-id="63181-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63181-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
