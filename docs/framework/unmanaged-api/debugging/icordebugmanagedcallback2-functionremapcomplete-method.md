---
title: ICorDebugManagedCallback2::FunctionRemapComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: d49992b1f4b25586f6171a51b351a25d453560f2
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212155"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="308ca-102">ICorDebugManagedCallback2::FunctionRemapComplete — Metoda</span><span class="sxs-lookup"><span data-stu-id="308ca-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>
<span data-ttu-id="308ca-103">Powiadamia debuger, że wykonywanie kodu zostało przełączone do nowej wersji edytowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="308ca-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="308ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="308ca-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="308ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="308ca-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="308ca-106">podczas Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji zawierającą edytowaną funkcję.</span><span class="sxs-lookup"><span data-stu-id="308ca-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="308ca-107">podczas Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek, w którym napotkano punkt przerwania mapowania.</span><span class="sxs-lookup"><span data-stu-id="308ca-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="308ca-108">podczas Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersję funkcji aktualnie uruchomionej w wątku.</span><span class="sxs-lookup"><span data-stu-id="308ca-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="308ca-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="308ca-109">Remarks</span></span>  
 <span data-ttu-id="308ca-110">To wywołanie zwrotne daje debugerowi możliwość ponownego utworzenia wszystkich, które wcześniej istniały.</span><span class="sxs-lookup"><span data-stu-id="308ca-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="308ca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="308ca-111">Requirements</span></span>  
 <span data-ttu-id="308ca-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="308ca-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="308ca-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="308ca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="308ca-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="308ca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="308ca-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="308ca-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308ca-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="308ca-116">See also</span></span>

- [<span data-ttu-id="308ca-117">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="308ca-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="308ca-118">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="308ca-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
