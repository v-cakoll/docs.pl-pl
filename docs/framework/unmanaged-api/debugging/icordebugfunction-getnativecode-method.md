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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1cb073c1f93c6d60d86e5160dcfb0cbdaf1cd33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414574"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="42226-102">ICorDebugFunction::GetNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="42226-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="42226-103">Pobiera kodu natywnego dla funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="42226-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42226-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42226-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42226-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42226-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="42226-106">[out] Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kodu natywnego dla tej funkcji, lub wartość null, jeśli ta funkcja jest kod języka pośredniego (MSIL) firmy Microsoft, który nie został just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="42226-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42226-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42226-107">Remarks</span></span>  
 <span data-ttu-id="42226-108">Jeśli funkcja reprezentowanym przez to `ICorDebugFunction` wystąpienia został skompilowany JIT więcej niż raz, jak w przypadku typów ogólnych `GetNativeCode` zwraca obiekt losowego kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="42226-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42226-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42226-109">Requirements</span></span>  
 <span data-ttu-id="42226-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42226-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42226-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42226-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42226-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42226-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42226-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42226-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
