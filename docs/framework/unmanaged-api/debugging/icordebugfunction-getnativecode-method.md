---
title: "ICorDebugFunction::GetNativeCode — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetNativeCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2fccfaeb346d59f5cf565f47a9a64e732706adad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="ada15-102">ICorDebugFunction::GetNativeCode — Metoda</span><span class="sxs-lookup"><span data-stu-id="ada15-102">ICorDebugFunction::GetNativeCode Method</span></span>
<span data-ttu-id="ada15-103">Pobiera kodu natywnego dla funkcji, która jest reprezentowana przez to wystąpienie ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="ada15-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada15-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ada15-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ada15-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ada15-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="ada15-106">[out] Wskaźnik do wystąpienia ICorDebugCode, który reprezentuje kodu natywnego dla tej funkcji, lub wartość null, jeśli ta funkcja jest kod języka pośredniego (MSIL) firmy Microsoft, który nie został just-in-time (JIT) skompilowany.</span><span class="sxs-lookup"><span data-stu-id="ada15-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada15-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ada15-107">Remarks</span></span>  
 <span data-ttu-id="ada15-108">Jeśli funkcja reprezentowanym przez to `ICorDebugFunction` wystąpienia został skompilowany JIT więcej niż raz, jak w przypadku typów ogólnych `GetNativeCode` zwraca obiekt losowego kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="ada15-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada15-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ada15-109">Requirements</span></span>  
 <span data-ttu-id="ada15-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada15-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada15-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ada15-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ada15-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ada15-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada15-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada15-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
