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
ms.openlocfilehash: 081852f91f243c4a979e2969220e71bd10c8c56b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212892"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="1988b-102">ICorDebugProcess::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="1988b-102">ICorDebugProcess::GetThread Method</span></span>
<span data-ttu-id="1988b-103">Pobiera wątek tego procesu, który ma określony identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1988b-103">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1988b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1988b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1988b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1988b-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="1988b-106">podczas Identyfikator wątku systemu operacyjnego wątku, który ma zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="1988b-106">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="1988b-107">określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek.</span><span class="sxs-lookup"><span data-stu-id="1988b-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1988b-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1988b-108">Requirements</span></span>  
 <span data-ttu-id="1988b-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1988b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1988b-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1988b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1988b-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1988b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1988b-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1988b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
