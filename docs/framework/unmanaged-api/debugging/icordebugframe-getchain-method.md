---
title: "ICorDebugFrame::GetChain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 479ad2db4752f9e031783b430396286c6989b115
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="0b57c-102">ICorDebugFrame::GetChain — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b57c-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="0b57c-103">Pobiera wskaźnik do tej ramki jest częścią łańcucha.</span><span class="sxs-lookup"><span data-stu-id="0b57c-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b57c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b57c-104">Syntax</span></span>  
  
```  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b57c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b57c-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="0b57c-106">[out] Wskaźnik do adresu ICorDebugChain obiekt, który reprezentuje łańcuch zawierający tej ramki.</span><span class="sxs-lookup"><span data-stu-id="0b57c-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b57c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b57c-107">Requirements</span></span>  
 <span data-ttu-id="0b57c-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b57c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b57c-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b57c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b57c-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b57c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b57c-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b57c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
