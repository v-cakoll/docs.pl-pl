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
ms.openlocfilehash: 82a7689bb1848d89f5dee4482d8dc7685c9c5b5c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378337"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="2f5f3-102">ICorDebugThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f5f3-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="2f5f3-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="2f5f3-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f5f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f5f3-104">Methods</span></span>  
  
|<span data-ttu-id="2f5f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f5f3-105">Method</span></span>|<span data-ttu-id="2f5f3-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2f5f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f5f3-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="2f5f3-107">Next Method</span></span>](icordebugthreadenum-next-method.md)|<span data-ttu-id="2f5f3-108">Pobiera określoną liczbę `ICorDebugThread` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="2f5f3-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f5f3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f5f3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f5f3-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2f5f3-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f5f3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f5f3-111">Requirements</span></span>  
 <span data-ttu-id="2f5f3-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5f3-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f5f3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f5f3-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f5f3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f5f3-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5f3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5f3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f5f3-116">See also</span></span>

- [<span data-ttu-id="2f5f3-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="2f5f3-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
