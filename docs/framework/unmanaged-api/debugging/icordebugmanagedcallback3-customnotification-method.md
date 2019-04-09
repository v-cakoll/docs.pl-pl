---
title: ICorDebugManagedCallback3::CustomNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193580"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="b3acf-102">ICorDebugManagedCallback3::CustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3acf-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="b3acf-103">Wskazuje, że zgłoszono powiadomienie niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="b3acf-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3acf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3acf-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3acf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3acf-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b3acf-106">[in] Wskaźnik do wątku, który spowodował zgłoszenie.</span><span class="sxs-lookup"><span data-stu-id="b3acf-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b3acf-107">[in] Wskaźnik do domeny aplikacji, która zawiera wątku, który spowodował zgłoszenie.</span><span class="sxs-lookup"><span data-stu-id="b3acf-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3acf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b3acf-108">Return Value</span></span>  
 <span data-ttu-id="b3acf-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="b3acf-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b3acf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3acf-110">HRESULT</span></span>|<span data-ttu-id="b3acf-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b3acf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3acf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3acf-112">S_OK</span></span>|<span data-ttu-id="b3acf-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b3acf-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b3acf-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="b3acf-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3acf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3acf-115">Remarks</span></span>  
 <span data-ttu-id="b3acf-116">Kolejne wywołanie [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) metoda pobiera obiekt wątku, który został przekazany do <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="b3acf-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b3acf-117">Typ obiektu wątku musi być wcześniej włączone przez wywołanie metody [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b3acf-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="b3acf-118">Debuger może odczytywać parametrach specyficznych dla typu pola obiektu wątku i mogą przechowywać odpowiedzi w polach.</span><span class="sxs-lookup"><span data-stu-id="b3acf-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="b3acf-119">[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interfejsu nakłada żadne zasady dotyczące typów powiadomień i ich zawartość, a semantyka powiadomienia są ściśle kontrakt między debugery, aplikacji i programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b3acf-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3acf-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3acf-120">Requirements</span></span>  
 <span data-ttu-id="b3acf-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3acf-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3acf-122">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3acf-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3acf-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3acf-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b3acf-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b3acf-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3acf-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3acf-125">See also</span></span>

- [<span data-ttu-id="b3acf-126">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b3acf-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="b3acf-127">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b3acf-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b3acf-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b3acf-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
