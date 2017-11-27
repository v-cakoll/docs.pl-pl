---
title: "ICorDebugThread::CreateStepper — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateStepper
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b66c3e536104a46b65c92fe038fb5a92d79db299
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="41248-102">ICorDebugThread::CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="41248-102">ICorDebugThread::CreateStepper Method</span></span>
<span data-ttu-id="41248-103">Tworzy obiekt ICorDebugStepper — umożliwiający krokowe aktywną ramkę tego ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="41248-103">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41248-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41248-104">Syntax</span></span>  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41248-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41248-105">Parameters</span></span>  
 `ppStepper`  
 <span data-ttu-id="41248-106">[out] Wskaźnik do adresu `ICorDebugStepper` obiekt, który umożliwia krokowe aktywną ramkę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="41248-106">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41248-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41248-107">Remarks</span></span>  
 <span data-ttu-id="41248-108">Aktywną ramkę może być kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="41248-108">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="41248-109">`ICorDebugStepper` Interfejs musi posłużyć do wykonania, rzeczywista krokowe wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="41248-109">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41248-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41248-110">Requirements</span></span>  
 <span data-ttu-id="41248-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41248-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41248-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41248-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41248-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41248-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41248-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41248-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
