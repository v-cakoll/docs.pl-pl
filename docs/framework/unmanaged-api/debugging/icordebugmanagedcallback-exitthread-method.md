---
title: ICorDebugManagedCallback::ExitThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 3ba1280aa44a9445f6af7fe9a8769b7cdc7edb66
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205248"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="b53a5-102">ICorDebugManagedCallback::ExitThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="b53a5-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="b53a5-103">Powiadamia debuger, że wątek wykonujący kod zarządzany został zakończony.</span><span class="sxs-lookup"><span data-stu-id="b53a5-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b53a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b53a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b53a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b53a5-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b53a5-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek.</span><span class="sxs-lookup"><span data-stu-id="b53a5-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="b53a5-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="b53a5-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b53a5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b53a5-108">Remarks</span></span>  
 <span data-ttu-id="b53a5-109">Po `ExitThread` wywołaniu wywołania zwrotnego wątek nie będzie już wyświetlany w wyliczeniach wątków.</span><span class="sxs-lookup"><span data-stu-id="b53a5-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b53a5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b53a5-110">Requirements</span></span>  
 <span data-ttu-id="b53a5-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b53a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b53a5-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b53a5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b53a5-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b53a5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b53a5-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b53a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53a5-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b53a5-115">See also</span></span>

- [<span data-ttu-id="b53a5-116">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b53a5-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
