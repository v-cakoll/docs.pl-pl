---
title: ICorDebugFunction::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184e578efb549a1dc2e9ec1e30a29ff289b68719
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="f7d79-102">ICorDebugFunction::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7d79-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="f7d79-103">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, którą ta funkcja jest elementem członkowskim.</span><span class="sxs-lookup"><span data-stu-id="f7d79-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d79-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7d79-104">Syntax</span></span>  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7d79-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7d79-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="f7d79-106">[out] Wskaźnik do adresu `ICorDebugClass` obiekt, który reprezentuje klasę lub wartość null, jeśli ta funkcja nie jest elementem członkowskim klasy.</span><span class="sxs-lookup"><span data-stu-id="f7d79-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d79-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7d79-107">Requirements</span></span>  
 <span data-ttu-id="f7d79-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d79-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d79-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7d79-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7d79-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7d79-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d79-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d79-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
