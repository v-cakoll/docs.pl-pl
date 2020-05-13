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
ms.openlocfilehash: d6ce5a5cc64a5eb805faa5bb17a42a662940affe
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210257"
---
# <a name="icordebugilframegetlocalvariable-method"></a><span data-ttu-id="8eeef-102">ICorDebugILFrame::GetLocalVariable — Metoda</span><span class="sxs-lookup"><span data-stu-id="8eeef-102">ICorDebugILFrame::GetLocalVariable Method</span></span>
<span data-ttu-id="8eeef-103">Pobiera wartość określonej zmiennej lokalnej w ramce stosu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8eeef-103">Gets the value of the specified local variable in this Microsoft intermediate language (MSIL) stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eeef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8eeef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eeef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8eeef-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="8eeef-106">podczas Indeks zmiennej lokalnej w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="8eeef-106">[in] The index of the local variable in this MSIL stack frame.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="8eeef-107">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje pobraną wartość.</span><span class="sxs-lookup"><span data-stu-id="8eeef-107">[out] A pointer to the address of an ICorDebugValue object that represents the retrieved value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eeef-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8eeef-108">Remarks</span></span>  
 <span data-ttu-id="8eeef-109">`GetLocalVariable`Metoda może być używana w ramce stosu MSIL lub w ramce skompilowanej just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="8eeef-109">The `GetLocalVariable` method can be used either in an MSIL stack frame or in a just-in-time (JIT) compiled frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eeef-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8eeef-110">Requirements</span></span>  
 <span data-ttu-id="8eeef-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eeef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eeef-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8eeef-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8eeef-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8eeef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8eeef-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eeef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
