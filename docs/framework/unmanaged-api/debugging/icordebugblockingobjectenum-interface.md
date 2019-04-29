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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a23d21d0ed8c6a6a226d5e58eafb7bde65a4896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645438"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="82015-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="82015-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="82015-103">Dostarcza moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="82015-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="82015-104">Ten interfejs jest podklasą icordebugenum — interfejs.</span><span class="sxs-lookup"><span data-stu-id="82015-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82015-105">Metody</span><span class="sxs-lookup"><span data-stu-id="82015-105">Methods</span></span>  
  
|<span data-ttu-id="82015-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="82015-106">Method</span></span>|<span data-ttu-id="82015-107">Opis</span><span class="sxs-lookup"><span data-stu-id="82015-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82015-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="82015-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="82015-109">Wylicza listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="82015-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82015-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82015-110">Remarks</span></span>  
 <span data-ttu-id="82015-111">Każdy `CorDebugBlockingObject` struktury reprezentuje obiekt, który blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="82015-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82015-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="82015-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82015-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82015-113">Requirements</span></span>  
 <span data-ttu-id="82015-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82015-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82015-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82015-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82015-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82015-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82015-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82015-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82015-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82015-118">See also</span></span>

- [<span data-ttu-id="82015-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="82015-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="82015-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="82015-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
