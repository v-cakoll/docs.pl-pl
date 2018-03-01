---
title: "ICorDebugInternalFrame::GetFrameType — Metoda"
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
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 476903ae8f1461a46d685bc3e549c3b6553d5c68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="0e3f5-102">ICorDebugInternalFrame::GetFrameType — Metoda</span><span class="sxs-lookup"><span data-stu-id="0e3f5-102">ICorDebugInternalFrame::GetFrameType Method</span></span>
<span data-ttu-id="0e3f5-103">Pobiera typ tej ramki wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0e3f5-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0e3f5-104">Syntax</span></span>  
  
```  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e3f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e3f5-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="0e3f5-106">[out] Wskaźnik do wartości wyliczenia CorDebugInternalFrameType wskazująca typ wewnętrzny ramki reprezentowany przez to `ICorDebugInternalFrame` obiektu.</span><span class="sxs-lookup"><span data-stu-id="0e3f5-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e3f5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e3f5-107">Remarks</span></span>  
 <span data-ttu-id="0e3f5-108">Typ ramki wewnętrzny nigdy nie będą STUBFRAME_NONE.</span><span class="sxs-lookup"><span data-stu-id="0e3f5-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="0e3f5-109">Debugery bezpiecznie ignorować typów nierozpoznany wewnętrzny ramek.</span><span class="sxs-lookup"><span data-stu-id="0e3f5-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e3f5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0e3f5-110">Requirements</span></span>  
 <span data-ttu-id="0e3f5-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e3f5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3f5-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e3f5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e3f5-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e3f5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e3f5-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3f5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
