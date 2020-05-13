---
title: ICorDebugManagedCallback::Breakpoint — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Breakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Breakpoint
helpviewer_keywords:
- ICorDebugManagedCallback::Breakpoint method [.NET Framework debugging]
- Breakpoint method [.NET Framework debugging]
ms.assetid: 60b279b0-a726-46d2-8c53-76986a007ebb
topic_type:
- apiref
ms.openlocfilehash: d8e62499a813419ecc30924624da553ca9f2c7b2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213403"
---
# <a name="icordebugmanagedcallbackbreakpoint-method"></a><span data-ttu-id="dc6ad-102">ICorDebugManagedCallback::Breakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="dc6ad-102">ICorDebugManagedCallback::Breakpoint Method</span></span>
<span data-ttu-id="dc6ad-103">Powiadamia debuger w przypadku napotkania punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-103">Notifies the debugger when a breakpoint is encountered.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc6ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc6ad-104">Syntax</span></span>  
  
```cpp  
HRESULT Breakpoint (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc6ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc6ad-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dc6ad-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, która zawiera punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the breakpoint.</span></span>  
  
 `pThread`  
 <span data-ttu-id="dc6ad-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, który zawiera punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the breakpoint.</span></span>  
  
 `pBreakpoint`  
 <span data-ttu-id="dc6ad-108">podczas Wskaźnik do obiektu ICorDebugBreakpoint, który reprezentuje punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="dc6ad-108">[in] A pointer to an ICorDebugBreakpoint object that represents the breakpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc6ad-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc6ad-109">Requirements</span></span>  
 <span data-ttu-id="dc6ad-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc6ad-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc6ad-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dc6ad-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc6ad-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dc6ad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc6ad-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc6ad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc6ad-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc6ad-114">See also</span></span>

- [<span data-ttu-id="dc6ad-115">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dc6ad-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
