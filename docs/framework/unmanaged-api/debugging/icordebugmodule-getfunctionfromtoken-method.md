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
ms.openlocfilehash: cb966a918c63b4fbc00dcf52819b9384427dfdaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129586"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a><span data-ttu-id="e3d16-102">ICorDebugModule::GetFunctionFromToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3d16-102">ICorDebugModule::GetFunctionFromToken Method</span></span>
<span data-ttu-id="e3d16-103">Pobiera funkcję określoną przez token metadanych.</span><span class="sxs-lookup"><span data-stu-id="e3d16-103">Gets the function that is specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3d16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3d16-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3d16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3d16-105">Parameters</span></span>  
 `methodDef`  
 <span data-ttu-id="e3d16-106">podczas `mdMethodDef` token metadanych, który odwołuje się do metadanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e3d16-106">[in] A `mdMethodDef` metadata token that references the function's metadata.</span></span>  
  
 `ppFunction`  
 <span data-ttu-id="e3d16-107">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugFunction, który reprezentuje funkcję.</span><span class="sxs-lookup"><span data-stu-id="e3d16-107">[out] A pointer to the address of a ICorDebugFunction interface object that represents the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3d16-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3d16-108">Remarks</span></span>  
 <span data-ttu-id="e3d16-109">Metoda `GetFunctionFromToken` zwraca wynik HRESULT CORDBG_E_FUNCTION_NOT_IL, jeśli wartość przeniesiona `methodDef` nie odwołuje się do metody MSIL.</span><span class="sxs-lookup"><span data-stu-id="e3d16-109">The `GetFunctionFromToken` method returns a CORDBG_E_FUNCTION_NOT_IL HRESULT if the value passed in `methodDef` does not refer to a Microsoft intermediate language (MSIL) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3d16-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3d16-110">Requirements</span></span>  
 <span data-ttu-id="e3d16-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3d16-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3d16-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e3d16-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3d16-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3d16-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3d16-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3d16-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
