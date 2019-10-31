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
ms.openlocfilehash: bbe2727e4b93cf6d7b3111b6060d170e497024a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130768"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="8cca3-102">ICorDebugManagedCallback::ExitThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="8cca3-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="8cca3-103">Powiadamia debuger, że wątek wykonujący kod zarządzany został zakończony.</span><span class="sxs-lookup"><span data-stu-id="8cca3-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cca3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cca3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cca3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8cca3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8cca3-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą zarządzany wątek.</span><span class="sxs-lookup"><span data-stu-id="8cca3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="8cca3-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8cca3-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cca3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cca3-108">Remarks</span></span>  
 <span data-ttu-id="8cca3-109">Po wywołaniu wywołania zwrotnego `ExitThread` wątek nie będzie już wyświetlany w wyliczeniach wątków.</span><span class="sxs-lookup"><span data-stu-id="8cca3-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cca3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8cca3-110">Requirements</span></span>  
 <span data-ttu-id="8cca3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cca3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cca3-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8cca3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cca3-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8cca3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cca3-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cca3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cca3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cca3-115">See also</span></span>

- [<span data-ttu-id="8cca3-116">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8cca3-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
