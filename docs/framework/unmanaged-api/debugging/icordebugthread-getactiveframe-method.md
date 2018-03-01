---
title: "ICorDebugThread::GetActiveFrame — Metoda"
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
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 441f97ebbaf95a8b6b6e14c8372893a83f6299a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="f0785-102">ICorDebugThread::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0785-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="f0785-103">Pobiera wskaźnika interfejsu do aktywnej ramki (najnowsze) dla tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f0785-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0785-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0785-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0785-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0785-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="f0785-106">[out] Wskaźnik do adresu ICorDebugFrame obiektu interfejsu, który reprezentuje ramkę.</span><span class="sxs-lookup"><span data-stu-id="f0785-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0785-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0785-107">Remarks</span></span>  
 <span data-ttu-id="f0785-108">`ppFrame` Parametr ma wartość null, jeśli ramka nie jest obecnie aktywne.</span><span class="sxs-lookup"><span data-stu-id="f0785-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0785-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0785-109">Requirements</span></span>  
 <span data-ttu-id="f0785-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0785-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0785-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0785-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0785-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0785-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0785-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0785-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
