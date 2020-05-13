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
ms.openlocfilehash: 48bfce9966ff12fe1b425fbcd9a81860628a54e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212675"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="d2ba4-102">ICorDebugManagedCallback::NameChange — Metoda</span><span class="sxs-lookup"><span data-stu-id="d2ba4-102">ICorDebugManagedCallback::NameChange Method</span></span>
<span data-ttu-id="d2ba4-103">Powiadamia debuger o zmianie nazwy domeny aplikacji lub wątku.</span><span class="sxs-lookup"><span data-stu-id="d2ba4-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2ba4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2ba4-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2ba4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2ba4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d2ba4-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, w której zmieniono nazwę lub zawierający wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="d2ba4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d2ba4-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który miał zmianę nazwy.</span><span class="sxs-lookup"><span data-stu-id="d2ba4-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2ba4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2ba4-108">Requirements</span></span>  
 <span data-ttu-id="d2ba4-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2ba4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2ba4-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2ba4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2ba4-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d2ba4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2ba4-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2ba4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ba4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2ba4-113">See also</span></span>

- [<span data-ttu-id="d2ba4-114">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d2ba4-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
