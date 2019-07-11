---
title: ICorDebugAppDomain2::GetFunctionPointerType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f0643ba9e750e7c64d2dae8eb5744df7bc26931
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737799"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a><span data-ttu-id="562b9-102">ICorDebugAppDomain2::GetFunctionPointerType — Metoda</span><span class="sxs-lookup"><span data-stu-id="562b9-102">ICorDebugAppDomain2::GetFunctionPointerType Method</span></span>
<span data-ttu-id="562b9-103">Pobiera wskaźnik do funkcji, która ma podpis danego.</span><span class="sxs-lookup"><span data-stu-id="562b9-103">Gets a pointer to a function that has a given signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562b9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="562b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="562b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="562b9-105">Parameters</span></span>  
 `nTypeArgs`  
 <span data-ttu-id="562b9-106">[in] Liczba argumentów typu dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="562b9-106">[in] The number of type arguments for the function.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="562b9-107">[in] Tablica wskaźników, z których każdy wskazuje na obiekt ICorDebugType, który reprezentuje argument typu funkcji.</span><span class="sxs-lookup"><span data-stu-id="562b9-107">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument of the function.</span></span> <span data-ttu-id="562b9-108">Pierwszy element jest typu zwracanego; Każdy z innymi elementami jest typ parametru.</span><span class="sxs-lookup"><span data-stu-id="562b9-108">The first element is the return type; each of the other elements is a parameter type.</span></span>  
  
 `ppType`  
 <span data-ttu-id="562b9-109">[out] Wskaźnik na adres `ICorDebugType` obiekt, który reprezentuje wskaźnik do funkcji.</span><span class="sxs-lookup"><span data-stu-id="562b9-109">[out] A pointer to the address of an `ICorDebugType` object that represents the pointer to the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="562b9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="562b9-110">Requirements</span></span>  
 <span data-ttu-id="562b9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="562b9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="562b9-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="562b9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="562b9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="562b9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="562b9-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="562b9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
