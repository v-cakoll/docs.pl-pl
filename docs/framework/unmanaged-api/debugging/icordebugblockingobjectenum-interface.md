---
title: ICorDebugBlockingObjectEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: 8be4332da77c3fbf4229a3fbeb9ba835a7a13eee
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894793"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="225c4-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="225c4-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="225c4-103">Dostarcza moduł wyliczający listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="225c4-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="225c4-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="225c4-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="225c4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="225c4-105">Methods</span></span>  
  
|<span data-ttu-id="225c4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="225c4-106">Method</span></span>|<span data-ttu-id="225c4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="225c4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="225c4-108">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="225c4-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="225c4-109">Wylicza listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="225c4-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="225c4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="225c4-110">Remarks</span></span>  
 <span data-ttu-id="225c4-111">Każda `CorDebugBlockingObject` struktura reprezentuje obiekt, który blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="225c4-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="225c4-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="225c4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225c4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="225c4-113">Requirements</span></span>  
 <span data-ttu-id="225c4-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="225c4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225c4-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="225c4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="225c4-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="225c4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="225c4-117">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225c4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="225c4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="225c4-118">See also</span></span>

- [<span data-ttu-id="225c4-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="225c4-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="225c4-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="225c4-120">Debugging</span></span>](index.md)
