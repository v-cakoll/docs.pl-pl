---
title: ICorDebugEval::GetResult — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667122"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="7dc09-102">ICorDebugEval::GetResult — Metoda</span><span class="sxs-lookup"><span data-stu-id="7dc09-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="7dc09-103">Pobiera wyniki tej oceny.</span><span class="sxs-lookup"><span data-stu-id="7dc09-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dc09-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dc09-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dc09-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7dc09-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="7dc09-106">[out] Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wyniki tej oceny, jeśli oceny zakończy się normalnie.</span><span class="sxs-lookup"><span data-stu-id="7dc09-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dc09-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7dc09-107">Remarks</span></span>  
 <span data-ttu-id="7dc09-108">`GetResult` Metoda jest prawidłowa tylko w przypadku, po zakończeniu okresu ewaluacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7dc09-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="7dc09-109">Jeśli ocena zakończy się normalnie, `ppResult` określa wyniki.</span><span class="sxs-lookup"><span data-stu-id="7dc09-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="7dc09-110">Jeśli kończy się z powodu wyjątku, wynik jest zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7dc09-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="7dc09-111">Jeśli ocena dla nowego obiektu, wynik jest odwołanie do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="7dc09-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dc09-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7dc09-112">Requirements</span></span>  
 <span data-ttu-id="7dc09-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dc09-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dc09-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7dc09-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dc09-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7dc09-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dc09-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dc09-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
