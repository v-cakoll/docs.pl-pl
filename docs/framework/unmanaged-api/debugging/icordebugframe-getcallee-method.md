---
title: "ICorDebugFrame::GetCallee — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54a26ad7d4818aae81b765ab4e6c0e5be821680e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="804c8-102">ICorDebugFrame::GetCallee — Metoda</span><span class="sxs-lookup"><span data-stu-id="804c8-102">ICorDebugFrame::GetCallee Method</span></span>
<span data-ttu-id="804c8-103">Pobiera wskaźnik do obiektu ICorDebugFrame w łańcuchu bieżącego, która wywołuje tej ramki.</span><span class="sxs-lookup"><span data-stu-id="804c8-103">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="804c8-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="804c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="804c8-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="804c8-106">[out] Wskaźnik do adresu `ICorDebugFrame` obiekt, który reprezentuje wywołane ramki.</span><span class="sxs-lookup"><span data-stu-id="804c8-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="804c8-107">Ta wartość ma wartość null, jeśli ramka wywołującego jest najbardziej ramki w łańcuchu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="804c8-107">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="804c8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="804c8-108">Requirements</span></span>  
 <span data-ttu-id="804c8-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="804c8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804c8-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="804c8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="804c8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="804c8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="804c8-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
