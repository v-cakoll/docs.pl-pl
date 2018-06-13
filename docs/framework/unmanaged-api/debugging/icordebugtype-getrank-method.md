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
ms.openlocfilehash: 9f112e0d064041a877963939b78029da08bbbed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417657"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="e42cf-102">ICorDebugType::GetRank — Metoda</span><span class="sxs-lookup"><span data-stu-id="e42cf-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="e42cf-103">Pobiera liczbę wymiarów w typie tablicy.</span><span class="sxs-lookup"><span data-stu-id="e42cf-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e42cf-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e42cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e42cf-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="e42cf-106">[out] Wskaźnik do liczby wymiarów.</span><span class="sxs-lookup"><span data-stu-id="e42cf-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e42cf-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e42cf-107">Requirements</span></span>  
 <span data-ttu-id="e42cf-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e42cf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42cf-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e42cf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e42cf-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e42cf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e42cf-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42cf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
