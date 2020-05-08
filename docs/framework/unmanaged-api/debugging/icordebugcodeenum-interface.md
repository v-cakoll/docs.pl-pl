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
ms.openlocfilehash: cce0efa925683b5361a5422112db3f8231e2dfb4
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893276"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="19f96-102">ICorDebugCodeEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="19f96-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="19f96-103">Implementuje metody "ICorDebugEnum" i wylicza tablice "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="19f96-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19f96-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19f96-104">Methods</span></span>  
  
|<span data-ttu-id="19f96-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19f96-105">Method</span></span>|<span data-ttu-id="19f96-106">Opis</span><span class="sxs-lookup"><span data-stu-id="19f96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19f96-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="19f96-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="19f96-108">Pobiera określoną liczbę `ICorDebugCode` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="19f96-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19f96-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19f96-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19f96-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="19f96-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19f96-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19f96-111">Requirements</span></span>  
 <span data-ttu-id="19f96-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19f96-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19f96-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19f96-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19f96-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="19f96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19f96-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19f96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19f96-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19f96-116">See also</span></span>

- [<span data-ttu-id="19f96-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="19f96-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
