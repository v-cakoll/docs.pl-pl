---
title: "ICorDebugFrame::GetCaller — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCaller
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f465dd123b517b347a29118f3092f244c2212cd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="70966-102">ICorDebugFrame::GetCaller — Metoda</span><span class="sxs-lookup"><span data-stu-id="70966-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="70966-103">Pobiera wskaźnik do obiektu ICorDebugFrame w łańcuchu bieżącego, która wywołuje tej ramki.</span><span class="sxs-lookup"><span data-stu-id="70966-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70966-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70966-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70966-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70966-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="70966-106">[out] Wskaźnik do adresu `ICorDebugFrame` obiekt, który reprezentuje wywołanie ramki.</span><span class="sxs-lookup"><span data-stu-id="70966-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="70966-107">Ta wartość ma wartość null, jeśli wywołane ramki jest najbardziej zewnętrznego ramki w łańcuchu bieżącej.</span><span class="sxs-lookup"><span data-stu-id="70966-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70966-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70966-108">Requirements</span></span>  
 <span data-ttu-id="70966-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70966-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70966-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70966-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70966-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70966-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70966-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70966-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
