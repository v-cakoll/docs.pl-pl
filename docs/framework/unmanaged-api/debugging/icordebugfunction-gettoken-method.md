---
title: ICorDebugFunction::GetToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4613e11896a34ed1a7fe91d4767fb38ac75aab8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754517"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="e28ce-102">ICorDebugFunction::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="e28ce-102">ICorDebugFunction::GetToken Method</span></span>
<span data-ttu-id="e28ce-103">Pobiera token metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e28ce-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e28ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e28ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e28ce-105">Parameters</span></span>  
 `pMethodDef`  
 <span data-ttu-id="e28ce-106">[out] Wskaźnik do `mdMethodDef` token, który odwołuje się do metadanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e28ce-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28ce-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e28ce-107">Requirements</span></span>  
 <span data-ttu-id="e28ce-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e28ce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28ce-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e28ce-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e28ce-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e28ce-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e28ce-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e28ce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
