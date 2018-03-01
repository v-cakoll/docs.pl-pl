---
title: "ICorDebugFunction::GetCurrentVersionNumber — Metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c230c8ca6da69b45d05b3319220eacfa6c1f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="97d70-102">ICorDebugFunction::GetCurrentVersionNumber — Metoda</span><span class="sxs-lookup"><span data-stu-id="97d70-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="97d70-103">Pobiera numer wersji najnowszej modyfikowanie funkcji reprezentowany przez ten obiekt ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="97d70-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d70-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97d70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d70-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="97d70-106">[out] Wskaźnik do wartości całkowitej, który jest numer wersji najnowszej edycji wykonanych dla tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="97d70-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97d70-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97d70-107">Remarks</span></span>  
 <span data-ttu-id="97d70-108">Numer wersji najnowszej edycji wykonanych dla tej funkcji może być większa niż numer wersji samej funkcji.</span><span class="sxs-lookup"><span data-stu-id="97d70-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="97d70-109">Użyj jednej [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) metody lub [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) metoda pobierania numer wersji funkcji.</span><span class="sxs-lookup"><span data-stu-id="97d70-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d70-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97d70-110">Requirements</span></span>  
 <span data-ttu-id="97d70-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d70-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97d70-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97d70-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97d70-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97d70-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
