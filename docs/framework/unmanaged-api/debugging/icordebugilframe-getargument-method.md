---
title: ICorDebugILFrame::GetArgument — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46852ed8ac53c3a7720edff4833f3dc3cce42bbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475791"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="c2d90-102">ICorDebugILFrame::GetArgument — Metoda</span><span class="sxs-lookup"><span data-stu-id="c2d90-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="c2d90-103">Pobiera wartość określonego argumentu w tej ramce stosu intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c2d90-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2d90-104">Syntax</span></span>  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2d90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2d90-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="c2d90-106">[in] Indeks argumentu w tej ramki stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="c2d90-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c2d90-107">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="c2d90-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2d90-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2d90-108">Remarks</span></span>  
 <span data-ttu-id="c2d90-109">`GetArgument` Metody można użyć w ramce stosu MSIL lub w ramce skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c2d90-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d90-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2d90-110">Requirements</span></span>  
 <span data-ttu-id="c2d90-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d90-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d90-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2d90-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2d90-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d90-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d90-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d90-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
