---
title: ICorDebugCode::IsIL — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a82606d90444c2d543065287780e42da4f8b4943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750270"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="de8be-102">ICorDebugCode::IsIL — Metoda</span><span class="sxs-lookup"><span data-stu-id="de8be-102">ICorDebugCode::IsIL Method</span></span>
<span data-ttu-id="de8be-103">Pobiera wartość wskazującą, czy to "ICorDebugCode" reprezentuje kod, który został skompilowany w języka Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="de8be-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de8be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de8be-104">Syntax</span></span>  
  
```  
HRESULT IsIL (  
    [out] BOOL       *pbIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de8be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de8be-105">Parameters</span></span>  
 `pbIL`  
 <span data-ttu-id="de8be-106">[out] `true` Jeśli `ICorDebugCode` reprezentuje kod, który został skompilowany w kodzie MSIL; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="de8be-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de8be-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de8be-107">Requirements</span></span>  
 <span data-ttu-id="de8be-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de8be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de8be-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de8be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de8be-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de8be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de8be-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de8be-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de8be-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de8be-112">See also</span></span>
