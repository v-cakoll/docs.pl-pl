---
title: "ICorDebugThread::GetActiveFrame — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8b5d9d42b7c3f7827ce938fdd3dffe57b00142c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="914aa-102">ICorDebugThread::GetActiveFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="914aa-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="914aa-103">Pobiera wskaźnika interfejsu do aktywnej ramki (najnowsze) dla tego obiektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="914aa-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="914aa-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="914aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="914aa-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="914aa-106">[out] Wskaźnik do adresu ICorDebugFrame obiektu interfejsu, który reprezentuje ramkę.</span><span class="sxs-lookup"><span data-stu-id="914aa-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="914aa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="914aa-107">Remarks</span></span>  
 <span data-ttu-id="914aa-108">`ppFrame` Parametr ma wartość null, jeśli ramka nie jest obecnie aktywne.</span><span class="sxs-lookup"><span data-stu-id="914aa-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914aa-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="914aa-109">Requirements</span></span>  
 <span data-ttu-id="914aa-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="914aa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914aa-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="914aa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="914aa-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914aa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914aa-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914aa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
