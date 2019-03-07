---
title: ICorDebugILFrame::GetLocalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd36f01297f24c050f84fb67e7673f8641fe206
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475245"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="91de0-102">ICorDebugILFrame::GetLocalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="91de0-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="91de0-103">Pobiera wartość określonej zmiennej lokalnej w tej ramki stosu intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="91de0-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91de0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91de0-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91de0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91de0-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="91de0-106">[in] Indeks zmiennej lokalnej w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="91de0-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="91de0-107">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="91de0-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91de0-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91de0-108">Remarks</span></span>  
 <span data-ttu-id="91de0-109">`GetLocalVariable` Metody można użyć w ramce stosu MSIL lub w ramce skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="91de0-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91de0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91de0-110">Requirements</span></span>  
 <span data-ttu-id="91de0-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91de0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91de0-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91de0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91de0-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91de0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91de0-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91de0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
