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
ms.openlocfilehash: 6bf73a4be40f1fbd8e9d37477907001604e8e4a6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128818"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="1a3d1-102">ICorDebugProcess::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a3d1-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="1a3d1-103">Pobiera wątek tego procesu, który ma określony identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1a3d1-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a3d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a3d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a3d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a3d1-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="1a3d1-106">podczas Identyfikator wątku systemu operacyjnego wątku, który ma zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="1a3d1-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="1a3d1-107">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek.</span><span class="sxs-lookup"><span data-stu-id="1a3d1-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a3d1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a3d1-108">Requirements</span></span>  
 <span data-ttu-id="1a3d1-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a3d1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a3d1-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a3d1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a3d1-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a3d1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a3d1-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a3d1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
