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
ms.openlocfilehash: 2d8fa00a1a998430a55b913cfa25624246eab967
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788360"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="ea457-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea457-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="ea457-103">Powiadamia debuger o zmianie nazwy domeny aplikacji lub wątku.</span><span class="sxs-lookup"><span data-stu-id="ea457-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea457-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea457-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea457-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea457-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="ea457-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której zmieniono nazwę lub zawierający wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="ea457-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="ea457-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="ea457-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea457-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea457-108">Requirements</span></span>  
 <span data-ttu-id="ea457-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea457-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea457-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea457-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea457-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea457-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea457-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea457-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea457-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea457-113">See also</span></span>

- [<span data-ttu-id="ea457-114">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea457-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
