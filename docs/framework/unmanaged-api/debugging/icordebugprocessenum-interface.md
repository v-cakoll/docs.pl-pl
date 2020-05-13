---
title: ICorDebugProcessEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
ms.openlocfilehash: 3a820381f1c4605d620d74a5915c3e08de69d9fb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210114"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="b2c64-102">ICorDebugProcessEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2c64-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="b2c64-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="b2c64-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2c64-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2c64-104">Methods</span></span>  
  
|<span data-ttu-id="b2c64-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2c64-105">Method</span></span>|<span data-ttu-id="b2c64-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b2c64-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2c64-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b2c64-107">Next Method</span></span>](icordebugprocessenum-next-method.md)|<span data-ttu-id="b2c64-108">Pobiera określoną liczbę `ICorDebugProcess` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="b2c64-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c64-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2c64-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2c64-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b2c64-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c64-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2c64-111">Requirements</span></span>  
 <span data-ttu-id="b2c64-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c64-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c64-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2c64-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2c64-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2c64-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c64-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c64-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c64-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2c64-116">See also</span></span>

- [<span data-ttu-id="b2c64-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2c64-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
