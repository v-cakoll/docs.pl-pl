---
title: ICorDebugFunction::GetNativeCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: 98aee38415709974d84873df50c39263490f2f23
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213273"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="76d24-102">ICorDebugFunction::GetNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="76d24-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="76d24-103">Pobiera kod natywny dla funkcji reprezentowanej przez to wystąpienie ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="76d24-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="76d24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76d24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76d24-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="76d24-106">określoną Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kod natywny dla tej funkcji, lub wartość null, jeśli ta funkcja jest kodem języka pośredniego firmy Microsoft (MSIL), który nie został skompilowany jako just-in-Time (JIT).</span><span class="sxs-lookup"><span data-stu-id="76d24-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76d24-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76d24-107">Remarks</span></span>  
 <span data-ttu-id="76d24-108">Jeśli funkcja reprezentowana przez to wystąpienie została skompilowana w trybie `ICorDebugFunction` JIT więcej niż raz, jak w przypadku typów ogólnych, `GetNativeCode` zwraca losowy obiekt kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="76d24-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76d24-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76d24-109">Requirements</span></span>  
 <span data-ttu-id="76d24-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76d24-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76d24-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76d24-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76d24-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="76d24-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76d24-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76d24-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
