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
ms.openlocfilehash: 9e9f627f1ba213f663f042d1107afd1eb05b56b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757866"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="568bb-102">ICorDebugILFrame::GetArgument — Metoda</span><span class="sxs-lookup"><span data-stu-id="568bb-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="568bb-103">Pobiera wartość określonego argumentu w tej ramce stosu intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="568bb-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="568bb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="568bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="568bb-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="568bb-106">[in] Indeks argumentu w tej ramki stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="568bb-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="568bb-107">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="568bb-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="568bb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="568bb-108">Remarks</span></span>  
 <span data-ttu-id="568bb-109">`GetArgument` Metody można użyć w ramce stosu MSIL lub w ramce skompilowany just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="568bb-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="568bb-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="568bb-110">Requirements</span></span>  
 <span data-ttu-id="568bb-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="568bb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="568bb-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="568bb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="568bb-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="568bb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="568bb-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="568bb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
