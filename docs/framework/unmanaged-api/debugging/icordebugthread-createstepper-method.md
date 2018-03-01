---
title: "ICorDebugThread::CreateStepper — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 869b1862e479c42c1ea43c90a276e95adcd5c321
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="1c088-102">ICorDebugThread::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c088-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="1c088-103">Tworzy obiekt ICorDebugStepper — umożliwiający krokowe aktywną ramkę tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1c088-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c088-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c088-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c088-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c088-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="1c088-106">[out] Wskaźnik do adresu `ICorDebugStepper` obiekt, który umożliwia krokowe aktywną ramkę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="1c088-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c088-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c088-107">Remarks</span></span>  
 <span data-ttu-id="1c088-108">Aktywną ramkę może być kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1c088-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="1c088-109">`ICorDebugStepper` Interfejs musi posłużyć do wykonania, rzeczywista krokowe wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="1c088-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c088-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c088-110">Requirements</span></span>  
 <span data-ttu-id="1c088-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c088-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c088-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c088-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c088-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c088-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c088-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c088-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
