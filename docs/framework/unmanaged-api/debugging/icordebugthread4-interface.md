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
ms.openlocfilehash: a0d6f3e109f92ad44eeeb1b1dec05e53015992a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378362"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="c0798-102">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c0798-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="c0798-103">Dostarcza informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="c0798-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0798-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c0798-104">Methods</span></span>  
  
|<span data-ttu-id="c0798-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0798-105">Method</span></span>|<span data-ttu-id="c0798-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c0798-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0798-107">GetBlockingObjects, metoda</span><span class="sxs-lookup"><span data-stu-id="c0798-107">GetBlockingObjects Method</span></span>](icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="c0798-108">Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="c0798-108">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="c0798-109">HadUnhandledException, metoda</span><span class="sxs-lookup"><span data-stu-id="c0798-109">HadUnhandledException Method</span></span>](icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="c0798-110">Wskazuje, czy wątek kiedykolwiek miał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c0798-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="c0798-111">GetCurrentCustomDebuggerNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="c0798-111">GetCurrentCustomDebuggerNotification Method</span></span>](icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="c0798-112">Pobiera bieżący obiekt [ICorDebugManagedCallback3:: CustomNotification —](icordebugmanagedcallback3-customnotification-method.md) w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c0798-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0798-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0798-113">Remarks</span></span>  
 <span data-ttu-id="c0798-114">Ten interfejs jest logicznym rozszerzeniem interfejsów ICorDebugThread, ICorDebugThread2 i [ICorDebugThread3](icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c0798-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0798-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c0798-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0798-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0798-116">Requirements</span></span>  
 <span data-ttu-id="c0798-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0798-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0798-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0798-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0798-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c0798-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0798-120">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0798-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0798-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0798-121">See also</span></span>

- [<span data-ttu-id="c0798-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c0798-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c0798-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c0798-123">Debugging</span></span>](index.md)
