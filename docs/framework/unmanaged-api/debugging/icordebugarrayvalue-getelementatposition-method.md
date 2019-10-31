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
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088416"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a><span data-ttu-id="43bf5-102">ICorDebugArrayValue::GetElementAtPosition — Metoda</span><span class="sxs-lookup"><span data-stu-id="43bf5-102">ICorDebugArrayValue::GetElementAtPosition Method</span></span>
<span data-ttu-id="43bf5-103">Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.</span><span class="sxs-lookup"><span data-stu-id="43bf5-103">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43bf5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43bf5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43bf5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43bf5-105">Parameters</span></span>  
 `nPosition`  
 <span data-ttu-id="43bf5-106">podczas Pozycja elementu, który ma zostać pobrany.</span><span class="sxs-lookup"><span data-stu-id="43bf5-106">[in] The position of the element to be retrieved.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="43bf5-107">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="43bf5-107">[out] A pointer to the address of an ICorDebugValue object that represents the value of the element.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43bf5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43bf5-108">Remarks</span></span>  
 <span data-ttu-id="43bf5-109">Układ tablicy wielowymiarowej jest zgodny z C++ stylem układu tablicy.</span><span class="sxs-lookup"><span data-stu-id="43bf5-109">The layout of a multi-dimension array follows the C++ style of array layout.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43bf5-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43bf5-110">Requirements</span></span>  
 <span data-ttu-id="43bf5-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43bf5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43bf5-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="43bf5-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43bf5-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="43bf5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43bf5-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43bf5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
