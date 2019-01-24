---
title: ICorDebugThread4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e583569e43ea58b37f33729bfa19eef1929fae3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517243"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="f1c44-102">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f1c44-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="f1c44-103">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="f1c44-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1c44-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f1c44-104">Methods</span></span>  
  
|<span data-ttu-id="f1c44-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f1c44-105">Method</span></span>|<span data-ttu-id="f1c44-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f1c44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1c44-107">GetBlockingObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="f1c44-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="f1c44-108">Zawiera wyliczenie uporządkowane [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="f1c44-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="f1c44-109">HadUnhandledException, metoda</span><span class="sxs-lookup"><span data-stu-id="f1c44-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="f1c44-110">Wskazuje, czy wątek nigdy nie miała nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f1c44-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="f1c44-111">GetCurrentCustomDebuggerNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="f1c44-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="f1c44-112">Pobiera bieżący [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) obiektu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="f1c44-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1c44-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1c44-113">Remarks</span></span>  
 <span data-ttu-id="f1c44-114">Ten interfejs jest logicznym rozszerzeniem ICorDebugThread, icordebugthread2 —, i [icordebugthread3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="f1c44-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1c44-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f1c44-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c44-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1c44-116">Requirements</span></span>  
 <span data-ttu-id="f1c44-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c44-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c44-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1c44-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1c44-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1c44-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1c44-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c44-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1c44-121">See also</span></span>
- [<span data-ttu-id="f1c44-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f1c44-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f1c44-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f1c44-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
