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
ms.openlocfilehash: a33b6ff308f3444496e5a1cb2e04f28e80305db5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212584"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="9cba9-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="9cba9-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="9cba9-103">Pobiera funkcję określoną przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="9cba9-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cba9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cba9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cba9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9cba9-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="9cba9-106">podczas `mdMethodDef`Token metadanych, który odwołuje się do metadanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="9cba9-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="9cba9-107">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugFunction, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="9cba9-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cba9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cba9-108">Remarks</span></span>  
 <span data-ttu-id="9cba9-109">`GetFunctionFromToken`Metoda zwraca CORDBG_E_FUNCTION_NOT_IL HRESULT, jeśli przeniesiona wartość nie `methodDef` odwołuje się do metody MSIL (Microsoft pośredni Language).</span><span class="sxs-lookup"><span data-stu-id="9cba9-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cba9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9cba9-110">Requirements</span></span>  
 <span data-ttu-id="9cba9-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cba9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cba9-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9cba9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cba9-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9cba9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cba9-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cba9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
