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
ms.openlocfilehash: 52bfe669d3b078657916554255a11cecfc07d484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085093"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="97afa-102">ICorDebugEval::GetResult — Metoda</span><span class="sxs-lookup"><span data-stu-id="97afa-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="97afa-103">Pobiera wyniki tej oceny.</span><span class="sxs-lookup"><span data-stu-id="97afa-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97afa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97afa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97afa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97afa-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="97afa-106">określoną Wskaźnik na adres obiektu ICorDebugValue, który reprezentuje wyniki tej oceny, jeśli Ocena zakończy się normalnie.</span><span class="sxs-lookup"><span data-stu-id="97afa-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97afa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97afa-107">Remarks</span></span>  
 <span data-ttu-id="97afa-108">Metoda `GetResult` jest prawidłowa tylko po zakończeniu obliczania.</span><span class="sxs-lookup"><span data-stu-id="97afa-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="97afa-109">Jeśli Ocena kończy się normalnie, `ppResult` określa wyniki.</span><span class="sxs-lookup"><span data-stu-id="97afa-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="97afa-110">Jeśli zakończy się wyjątek, wynikiem jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="97afa-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="97afa-111">Jeśli Ocena dotyczyła nowego obiektu, wynik jest odwołaniem do nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="97afa-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97afa-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97afa-112">Requirements</span></span>  
 <span data-ttu-id="97afa-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97afa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97afa-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="97afa-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97afa-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="97afa-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97afa-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97afa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
