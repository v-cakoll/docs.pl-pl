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
ms.openlocfilehash: bfd61d985eac3ab56d8a5df9474b2b1a9f641f3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122844"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="34963-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="34963-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="34963-103">Dostarcza moduł wyliczający listę struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="34963-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="34963-104">Ten interfejs jest podklasą interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="34963-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34963-105">Metody</span><span class="sxs-lookup"><span data-stu-id="34963-105">Methods</span></span>  
  
|<span data-ttu-id="34963-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="34963-106">Method</span></span>|<span data-ttu-id="34963-107">Opis</span><span class="sxs-lookup"><span data-stu-id="34963-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34963-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="34963-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="34963-109">Wylicza listę struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="34963-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34963-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34963-110">Remarks</span></span>  
 <span data-ttu-id="34963-111">Każda struktura `CorDebugBlockingObject` reprezentuje obiekt, który blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="34963-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34963-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="34963-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34963-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34963-113">Requirements</span></span>  
 <span data-ttu-id="34963-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34963-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34963-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34963-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34963-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34963-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34963-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34963-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34963-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34963-118">See also</span></span>

- [<span data-ttu-id="34963-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="34963-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="34963-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="34963-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
