---
title: "ICorDebugCode::IsIL — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.IsIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 07b0490e322c70763a37b86fbb02e2f8b99bd768
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="7cf68-102">ICorDebugCode::IsIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="7cf68-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="7cf68-103">Pobiera wartość wskazującą, czy to "ICorDebugCode" reprezentuje kod, który został skompilowany w języku pośrednim firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7cf68-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf68-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cf68-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7cf68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7cf68-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="7cf68-106">[out] `true` Jeśli `ICorDebugCode` reprezentuje kod, który został skompilowany w MSIL; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7cf68-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf68-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cf68-107">Requirements</span></span>  
 <span data-ttu-id="7cf68-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf68-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf68-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cf68-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cf68-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cf68-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cf68-111">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf68-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf68-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cf68-112">See Also</span></span>  
 
