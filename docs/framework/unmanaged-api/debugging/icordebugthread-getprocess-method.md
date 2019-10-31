---
title: ICorDebugThread::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 8928e22b70af0360660c30289ee999a3e4c5e99e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133475"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="3ad6e-102">ICorDebugThread::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ad6e-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="3ad6e-103">Pobiera wskaźnik interfejsu do procesu, którego częścią jest ten ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="3ad6e-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ad6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ad6e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ad6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ad6e-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="3ad6e-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugProcess, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="3ad6e-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ad6e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ad6e-107">Requirements</span></span>  
 <span data-ttu-id="3ad6e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ad6e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ad6e-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ad6e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ad6e-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ad6e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ad6e-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ad6e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
