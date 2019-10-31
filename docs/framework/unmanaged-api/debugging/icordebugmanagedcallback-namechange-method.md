---
title: ICorDebugManagedCallback::NameChange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 456a79ec290964df8e9f74fc6ca19ef9aabe1230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130678"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="1c7bf-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c7bf-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="1c7bf-103">Powiadamia debuger o zmianie nazwy domeny aplikacji lub wątku.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c7bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c7bf-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c7bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c7bf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1c7bf-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której zmieniono nazwę lub zawierający wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="1c7bf-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c7bf-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c7bf-108">Requirements</span></span>  
 <span data-ttu-id="1c7bf-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c7bf-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c7bf-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c7bf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c7bf-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c7bf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c7bf-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c7bf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7bf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c7bf-113">See also</span></span>

- [<span data-ttu-id="1c7bf-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c7bf-114">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
