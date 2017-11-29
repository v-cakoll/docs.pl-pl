---
title: "ICorDebugFrame::GetCode — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetCode
helpviewer_keywords:
- GetCode method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCode method [.NET Framework debugging]
ms.assetid: fbaa0794-a031-4015-8beb-2749e47ac340
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4538526f0358e7fa5259e87cbdf46abdb662475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetcode-method"></a><span data-ttu-id="7a3b6-102">ICorDebugFrame::GetCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="7a3b6-102">ICorDebugFrame::GetCode Method</span></span>
<span data-ttu-id="7a3b6-103">Pobiera wskaźnik do kodu skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="7a3b6-103">Gets a pointer to the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a3b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a3b6-104">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [out] ICorDebugCode      **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a3b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7a3b6-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="7a3b6-106">[out] Wskaźnik do adresu ICorDebugCode obiektu, który reprezentuje kod skojarzone z tej ramki.</span><span class="sxs-lookup"><span data-stu-id="7a3b6-106">[out] A pointer to the address of an ICorDebugCode object that represents the code associated with this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3b6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a3b6-107">Requirements</span></span>  
 <span data-ttu-id="7a3b6-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3b6-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a3b6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a3b6-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a3b6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3b6-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
