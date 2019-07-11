---
title: ICorDebugType::GetRank — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e42db5d7ebc9ec9983fe9e56477808415b26968b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751570"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="d5c00-102">ICorDebugType::GetRank — Metoda</span><span class="sxs-lookup"><span data-stu-id="d5c00-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="d5c00-103">Pobiera liczbę wymiarów typu tablicowego.</span><span class="sxs-lookup"><span data-stu-id="d5c00-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5c00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5c00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5c00-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="d5c00-106">[out] Wskaźnik do liczby wymiarów.</span><span class="sxs-lookup"><span data-stu-id="d5c00-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c00-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5c00-107">Requirements</span></span>  
 <span data-ttu-id="d5c00-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c00-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c00-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5c00-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c00-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5c00-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c00-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c00-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
