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
ms.openlocfilehash: d715f5842bb7f75da5311d34bf7d4596f0801a92
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210283"
---
# <a name="icordebugilframegetargument-method"></a><span data-ttu-id="c6aee-102">ICorDebugILFrame::GetArgument — Metoda</span><span class="sxs-lookup"><span data-stu-id="c6aee-102">ICorDebugILFrame::GetArgument Method</span></span>
<span data-ttu-id="c6aee-103">Pobiera wartość określonego argumentu w ramce stosu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6aee-103">Gets the value of the specified argument in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6aee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6aee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6aee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6aee-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="c6aee-106">podczas Indeks argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="c6aee-106">[in] The index of the argument in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c6aee-107">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="c6aee-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6aee-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6aee-108">Remarks</span></span>  
 <span data-ttu-id="c6aee-109">`GetArgument`Metoda może być używana w ramce stosu MSIL lub w ramce skompilowanej just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="c6aee-109">The `GetArgument` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6aee-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6aee-110">Requirements</span></span>  
 <span data-ttu-id="c6aee-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6aee-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6aee-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c6aee-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6aee-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c6aee-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6aee-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6aee-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
