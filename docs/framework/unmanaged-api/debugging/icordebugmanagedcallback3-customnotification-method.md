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
ms.openlocfilehash: 078f90387a475559067d402610ec264f4076ae01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793265"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="487ea-102">ICorDebugManagedCallback3::CustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="487ea-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="487ea-103">Wskazuje, że zostało zgłoszone powiadomienie niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="487ea-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="487ea-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="487ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="487ea-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="487ea-106">podczas Wskaźnik do wątku, który wywołał powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="487ea-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="487ea-107">podczas Wskaźnik do domeny aplikacji zawierającej wątek, który zgłosił powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="487ea-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="487ea-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="487ea-108">Return Value</span></span>  
 <span data-ttu-id="487ea-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="487ea-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="487ea-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="487ea-110">HRESULT</span></span>|<span data-ttu-id="487ea-111">Opis</span><span class="sxs-lookup"><span data-stu-id="487ea-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="487ea-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="487ea-112">S_OK</span></span>|<span data-ttu-id="487ea-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="487ea-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="487ea-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="487ea-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="487ea-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="487ea-115">Remarks</span></span>  
 <span data-ttu-id="487ea-116">Kolejne wywołanie metody [ICorDebugThread4:: GetCurrentCustomDebuggerNotification —](icordebugthread4-getcurrentcustomdebuggernotification-method.md) powoduje pobranie obiektu wątku, który został przesłany do metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="487ea-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="487ea-117">Typ obiektu wątku musi być wcześniej włączony przez wywołanie metody [ICorDebugProcess3:: SetEnableCustomNotification —](icordebugprocess3-setenablecustomnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="487ea-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="487ea-118">Debuger może odczytać parametry specyficzne dla typu z pól obiektu wątku i może przechowywać odpowiedzi w polach.</span><span class="sxs-lookup"><span data-stu-id="487ea-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="487ea-119">Interfejs [ICorDebug](icordebug-interface.md) nie nakłada żadnych zasad dotyczących typów powiadomień ani ich zawartości, a semantyka powiadomień jest ściśle umową między debugerami, aplikacjami i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="487ea-119">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="487ea-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="487ea-120">Requirements</span></span>  
 <span data-ttu-id="487ea-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="487ea-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487ea-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="487ea-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="487ea-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="487ea-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="487ea-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487ea-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487ea-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="487ea-125">See also</span></span>

- [<span data-ttu-id="487ea-126">ICorDebugManagedCallback3, interfejs</span><span class="sxs-lookup"><span data-stu-id="487ea-126">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="487ea-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="487ea-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="487ea-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="487ea-128">Debugging</span></span>](index.md)
