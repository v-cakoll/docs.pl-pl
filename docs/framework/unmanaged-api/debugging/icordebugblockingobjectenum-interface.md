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
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778001"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="15e6f-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="15e6f-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="15e6f-103">Dostarcza moduł wyliczający listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="15e6f-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="15e6f-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="15e6f-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15e6f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="15e6f-105">Methods</span></span>  
  
|<span data-ttu-id="15e6f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="15e6f-106">Method</span></span>|<span data-ttu-id="15e6f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="15e6f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15e6f-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="15e6f-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="15e6f-109">Wylicza listę struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="15e6f-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e6f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15e6f-110">Remarks</span></span>  
 <span data-ttu-id="15e6f-111">Każda struktura `CorDebugBlockingObject` reprezentuje obiekt, który blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="15e6f-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15e6f-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="15e6f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e6f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15e6f-113">Requirements</span></span>  
 <span data-ttu-id="15e6f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15e6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e6f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="15e6f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15e6f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="15e6f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15e6f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e6f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15e6f-118">See also</span></span>

- [<span data-ttu-id="15e6f-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="15e6f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="15e6f-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="15e6f-120">Debugging</span></span>](index.md)
