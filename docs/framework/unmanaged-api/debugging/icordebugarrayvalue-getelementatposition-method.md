---
title: ICorDebugArrayValue::GetElementAtPosition — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: 5644c20ec5df2606c7258131573691997f424e50
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895013"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="98cc8-102">ICorDebugArrayValue::GetElementAtPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="98cc8-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="98cc8-103">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="98cc8-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cc8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98cc8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98cc8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98cc8-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="98cc8-106">podczas Pozycja elementu, który ma zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="98cc8-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="98cc8-107">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="98cc8-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98cc8-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98cc8-108">Remarks</span></span>  
 <span data-ttu-id="98cc8-109">Układ tablicy wielowymiarowej jest zgodny z stylem C++ układu tablicy.</span><span class="sxs-lookup"><span data-stu-id="98cc8-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cc8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98cc8-110">Requirements</span></span>  
 <span data-ttu-id="98cc8-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98cc8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cc8-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98cc8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98cc8-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98cc8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cc8-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cc8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
