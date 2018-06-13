---
title: ICorDebugModule::GetFunctionFromToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acffd24ae9d5aad5f48058eec036f912ee016289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415987"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="63a70-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="63a70-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="63a70-103">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="63a70-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63a70-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63a70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="63a70-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="63a70-106">[in] A `mdMethodDef` token metadanych, który odwołuje się do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="63a70-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="63a70-107">[out] Wskaźnik do adresu ICorDebugFunction obiektu interfejsu, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="63a70-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63a70-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63a70-108">Remarks</span></span>  
 <span data-ttu-id="63a70-109">`GetFunctionFromToken` Metoda zwróci wartość CORDBG_E_FUNCTION_NOT_IL HRESULT przypadku przekazano wartość `methodDef` nie odwołuje się do metody język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="63a70-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63a70-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63a70-110">Requirements</span></span>  
 <span data-ttu-id="63a70-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63a70-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a70-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63a70-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63a70-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63a70-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63a70-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a70-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
