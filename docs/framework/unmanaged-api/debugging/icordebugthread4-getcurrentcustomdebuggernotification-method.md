---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0529dee17469018e872951740a5899ef8664300a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421005"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="c9df4-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9df4-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="c9df4-103">Pobiera bieżący [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) obiektu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c9df4-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9df4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9df4-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9df4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9df4-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="c9df4-106">[out] Wskaźnik do bieżącego `ICorDebugManagedCallback3::CustomNotification` obiektu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="c9df4-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9df4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9df4-107">Remarks</span></span>  
 <span data-ttu-id="c9df4-108">Wartość `ppNotificationObject` ma wartość null, jeśli metoda nie jest wywoływana z poziomu `ICorDebugManagedCallback3::CustomNotification` wywołania zwrotnego, lub jeśli nie istnieje żaden bieżący obiekt powiadomień.</span><span class="sxs-lookup"><span data-stu-id="c9df4-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9df4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9df4-109">Requirements</span></span>  
 <span data-ttu-id="c9df4-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9df4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9df4-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9df4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9df4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9df4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9df4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9df4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9df4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9df4-114">See Also</span></span>  
 [<span data-ttu-id="c9df4-115">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9df4-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="c9df4-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c9df4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c9df4-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c9df4-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
