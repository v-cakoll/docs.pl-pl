---
title: ICorDebugProcess::GetThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5cbdd19fa14a41d8bd2eadec80dbafcea7b720d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766430"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="9f733-102">ICorDebugProcess::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f733-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="9f733-103">Pobiera wątku tego procesu, który ma identyfikator wątku określonego systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="9f733-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f733-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f733-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f733-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f733-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="9f733-106">[in] System operacyjny, wątek identyfikator wątku do pobrania.</span><span class="sxs-lookup"><span data-stu-id="9f733-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="9f733-107">[out] Wskaźnik na adres ICorDebugThread obiekt, który reprezentuje wątku.</span><span class="sxs-lookup"><span data-stu-id="9f733-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f733-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f733-108">Requirements</span></span>  
 <span data-ttu-id="9f733-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f733-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f733-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f733-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f733-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f733-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f733-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f733-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
