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
ms.openlocfilehash: 7a089831c39c36b0f8a0c7746e95a96e4ddfc5d9
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209399"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="5943e-102">ICorDebugFunction::GetClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="5943e-102">ICorDebugFunction::GetClass Method</span></span>
<span data-ttu-id="5943e-103">Pobiera obiekt ICorDebugClass, który reprezentuje klasę, do której należy ta funkcja.</span><span class="sxs-lookup"><span data-stu-id="5943e-103">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5943e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5943e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5943e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5943e-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="5943e-106">określoną Wskaźnik do adresu `ICorDebugClass` obiektu, który reprezentuje klasę lub wartość null, jeśli ta funkcja nie jest elementem członkowskim klasy.</span><span class="sxs-lookup"><span data-stu-id="5943e-106">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5943e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5943e-107">Requirements</span></span>  
 <span data-ttu-id="5943e-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5943e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5943e-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5943e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5943e-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5943e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5943e-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5943e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
