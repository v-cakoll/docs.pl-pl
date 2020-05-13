---
title: ICorDebugThread2::GetVolatileOSThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
ms.openlocfilehash: e8d59d617efa7656a3034d5c5e009a46b6121cdb
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377659"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="3ceaa-102">ICorDebugThread2::GetVolatileOSThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ceaa-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="3ceaa-103">Pobiera identyfikator wątku systemu operacyjnego dla tego ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="3ceaa-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ceaa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ceaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ceaa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ceaa-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="3ceaa-106">określoną Identyfikator wątku systemu operacyjnego dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="3ceaa-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ceaa-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ceaa-107">Requirements</span></span>  
 <span data-ttu-id="3ceaa-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ceaa-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ceaa-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ceaa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ceaa-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ceaa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ceaa-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ceaa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
