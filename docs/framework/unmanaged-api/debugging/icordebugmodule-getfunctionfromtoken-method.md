---
title: "ICorDebugModule::GetFunctionFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetFunctionFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c449b49333de562cd5ed07f827da6bc295e9c3c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="14a83-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="14a83-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="14a83-103">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="14a83-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a83-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14a83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a83-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="14a83-106">[in] A `mdMethodDef` token metadanych, który odwołuje się do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="14a83-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="14a83-107">[out] Wskaźnik do adresu ICorDebugFunction obiektu interfejsu, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="14a83-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14a83-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14a83-108">Remarks</span></span>  
 <span data-ttu-id="14a83-109">`GetFunctionFromToken` Metoda zwróci wartość CORDBG_E_FUNCTION_NOT_IL HRESULT przypadku przekazano wartość `methodDef` nie odwołuje się do metody język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14a83-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a83-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14a83-110">Requirements</span></span>  
 <span data-ttu-id="14a83-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a83-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a83-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14a83-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14a83-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a83-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a83-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a83-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
