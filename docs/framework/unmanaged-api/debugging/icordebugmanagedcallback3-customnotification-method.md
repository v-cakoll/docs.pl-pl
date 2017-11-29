---
title: "ICorDebugManagedCallback3::CustomNotification — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback3.CustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edff9c4b19131fcdfd4510c4020612acb43b6305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="36d91-102">ICorDebugManagedCallback3::CustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="36d91-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="36d91-103">Wskazuje powiadomienie niestandardowych debuger został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="36d91-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d91-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36d91-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36d91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36d91-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="36d91-106">[in] Wskaźnik do wątku, który uruchamiany powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="36d91-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="36d91-107">[in] Wskaźnik do domeny aplikacji, która zawiera wątku, który uruchamiany powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="36d91-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36d91-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="36d91-108">Return Value</span></span>  
 <span data-ttu-id="36d91-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="36d91-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="36d91-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36d91-110">HRESULT</span></span>|<span data-ttu-id="36d91-111">Opis</span><span class="sxs-lookup"><span data-stu-id="36d91-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36d91-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="36d91-112">S_OK</span></span>|<span data-ttu-id="36d91-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="36d91-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="36d91-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="36d91-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d91-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36d91-115">Remarks</span></span>  
 <span data-ttu-id="36d91-116">Kolejne wywołania [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda pobiera obiekt wątku, który został przekazany do <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="36d91-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="36d91-117">Typ obiektu wątek musi być wcześniej włączone przez wywołanie metody [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="36d91-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="36d91-118">Debuger może odczytywać parametry specyficzne dla typu pola obiektu wątku i może przechowywać odpowiedzi do pól.</span><span class="sxs-lookup"><span data-stu-id="36d91-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="36d91-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu nakłada żadnych zasad na typy powiadomień i ich zawartość i semantykę powiadomienia są ściśle kontraktu między debugery, aplikacji i programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36d91-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d91-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36d91-120">Requirements</span></span>  
 <span data-ttu-id="36d91-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d91-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d91-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36d91-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36d91-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36d91-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d91-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d91-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d91-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36d91-125">See Also</span></span>  
 [<span data-ttu-id="36d91-126">ICorDebugManagedCallback3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="36d91-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="36d91-127">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="36d91-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="36d91-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="36d91-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
