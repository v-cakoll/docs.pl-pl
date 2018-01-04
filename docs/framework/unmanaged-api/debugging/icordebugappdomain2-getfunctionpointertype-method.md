---
title: "ICorDebugAppDomain2::GetFunctionPointerType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetFunctionPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12cb3e62454aacacc69207ce3675448ea8c2ffee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="3a2c4-102">ICorDebugAppDomain2::GetFunctionPointerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a2c4-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="3a2c4-103">Pobiera wskaźnik do funkcji, która ma danym podpisem.</span><span class="sxs-lookup"><span data-stu-id="3a2c4-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a2c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a2c4-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a2c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a2c4-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="3a2c4-106">[in] Liczba argumentów typu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="3a2c4-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="3a2c4-107">[in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje typ argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="3a2c4-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="3a2c4-108">Pierwszy element jest typu zwracanego; Każdy z innymi elementami jest typ parametru.</span><span class="sxs-lookup"><span data-stu-id="3a2c4-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="3a2c4-109">[out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje wskaźnik do funkcji.</span><span class="sxs-lookup"><span data-stu-id="3a2c4-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a2c4-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a2c4-110">Requirements</span></span>  
 <span data-ttu-id="3a2c4-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a2c4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a2c4-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a2c4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a2c4-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a2c4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a2c4-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a2c4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
