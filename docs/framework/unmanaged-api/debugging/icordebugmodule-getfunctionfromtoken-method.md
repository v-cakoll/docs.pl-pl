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
ms.openlocfilehash: 547986633172d6f5e6549ad2048833dc9fb0cef3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763467"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="130f9-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="130f9-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="130f9-103">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="130f9-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="130f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="130f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="130f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="130f9-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="130f9-106">[in] A `mdMethodDef` token metadanych, który odwołuje się do metadanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="130f9-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="130f9-107">[out] Wskaźnik na adres obiektu interfejsu ICorDebugFunction, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="130f9-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="130f9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="130f9-108">Remarks</span></span>  
 <span data-ttu-id="130f9-109">`GetFunctionFromToken` Metoda zwraca wartość CORDBG_E_FUNCTION_NOT_IL HRESULT, jeśli wartość przekazywana w `methodDef` nie odwołuje się do firmy Microsoft intermediate language (MSIL) metody.</span><span class="sxs-lookup"><span data-stu-id="130f9-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="130f9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="130f9-110">Requirements</span></span>  
 <span data-ttu-id="130f9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="130f9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="130f9-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="130f9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="130f9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="130f9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="130f9-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="130f9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
