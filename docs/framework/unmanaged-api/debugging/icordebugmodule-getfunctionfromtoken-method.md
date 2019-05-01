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
ms.openlocfilehash: c1af0f8f792c856c0b27b4d3d9ff557bcc5fce82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994867"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="2fad1-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fad1-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="2fad1-103">Pobiera funkcję, która jest określona przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="2fad1-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fad1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fad1-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2fad1-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="2fad1-106">[in] A `mdMethodDef` token metadanych, który odwołuje się do metadanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="2fad1-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="2fad1-107">[out] Wskaźnik na adres obiektu interfejsu ICorDebugFunction, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="2fad1-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fad1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fad1-108">Remarks</span></span>  
 <span data-ttu-id="2fad1-109">`GetFunctionFromToken` Metoda zwraca wartość CORDBG_E_FUNCTION_NOT_IL HRESULT, jeśli wartość przekazywana w `methodDef` nie odwołuje się do firmy Microsoft intermediate language (MSIL) metody.</span><span class="sxs-lookup"><span data-stu-id="2fad1-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fad1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fad1-110">Requirements</span></span>  
 <span data-ttu-id="2fad1-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fad1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fad1-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fad1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fad1-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fad1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fad1-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fad1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
