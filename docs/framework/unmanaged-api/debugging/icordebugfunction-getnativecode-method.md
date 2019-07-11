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
ms.openlocfilehash: c0507d59011f6b584ecb1ae11c35c456c80793af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754596"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="df74e-102">ICorDebugFunction::GetNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="df74e-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="df74e-103">Pobiera kodu natywnego dla funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="df74e-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df74e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df74e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df74e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df74e-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="df74e-106">[out] Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kodu natywnego dla funkcji lub wartość null, jeśli ta funkcja jest kod intermediate language (MSIL) firmy Microsoft, który nie został just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="df74e-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df74e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df74e-107">Remarks</span></span>  
 <span data-ttu-id="df74e-108">Jeśli funkcja, która jest reprezentowana przez to `ICorDebugFunction` wystąpienie zostało kompilowanego dokładnie na czas więcej niż raz, jak w przypadku typów ogólnych `GetNativeCode` zwraca obiekt losowy kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="df74e-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df74e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df74e-109">Requirements</span></span>  
 <span data-ttu-id="df74e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df74e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df74e-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df74e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df74e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df74e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df74e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df74e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
