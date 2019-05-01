---
title: ICorDebugFunction::GetCurrentVersionNumber — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea615eacb30fd4e7a0fd7d730094c2ab4f9dc285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988731"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="e1615-102">ICorDebugFunction::GetCurrentVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1615-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="e1615-103">Pobiera numer wersji najnowszej edycji wprowadzone w funkcji reprezentowany przez ten obiekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="e1615-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1615-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1615-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1615-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1615-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="e1615-106">[out] Wskaźnik do wartości całkowitej, która jest numer wersji najnowszej edycji wykonanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1615-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1615-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1615-107">Remarks</span></span>  
 <span data-ttu-id="e1615-108">Numer wersji najnowszej edycji wykonanych dla tej funkcji może być większy niż numer wersji samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1615-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="e1615-109">Użyj jednej [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) metody lub [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metodę, która pobierze numer wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="e1615-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1615-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1615-110">Requirements</span></span>  
 <span data-ttu-id="e1615-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1615-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1615-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1615-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1615-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1615-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1615-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1615-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
