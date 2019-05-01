---
title: ICorDebugEval::IsActive — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::IsActive method [.NET Framework debugging]
ms.assetid: bf2bba24-d278-43bd-b1c5-35680e748d3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d992ea86b3221af222bb01f1985fe277cea5a2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989000"
---
# <a name="icordebugevalisactive-method"></a><span data-ttu-id="1eb36-102">ICorDebugEval::IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="1eb36-102">ICorDebugEval::IsActive Method</span></span>
<span data-ttu-id="1eb36-103">Pobiera wartość wskazującą, czy ten obiekt ICorDebugEval jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1eb36-103">Gets a value that indicates whether this ICorDebugEval object is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eb36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1eb36-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL              *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eb36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1eb36-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="1eb36-106">[out] Wskaźnik na wartość, która wskazuje, czy ta ocena jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="1eb36-106">[out] Pointer to a value that indicates whether this evaluation is active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eb36-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1eb36-107">Requirements</span></span>  
 <span data-ttu-id="1eb36-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1eb36-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eb36-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eb36-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eb36-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eb36-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eb36-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eb36-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
