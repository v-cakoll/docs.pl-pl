---
title: ICorDebugArrayValue::GetElement — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: 3d45caae56403d77776f1a8adbb5fb9c368ff105
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088489"
---
# <a name="icordebugarrayvaluegetelement-method"></a><span data-ttu-id="9d63c-102">ICorDebugArrayValue::GetElement — Metoda</span><span class="sxs-lookup"><span data-stu-id="9d63c-102">ICorDebugArrayValue::GetElement Method</span></span>
<span data-ttu-id="9d63c-103">Pobiera wartość danego elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="9d63c-103">Gets the value of the given array element.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d63c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d63c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]   
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d63c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d63c-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="9d63c-106">podczas Liczba wymiarów tego obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="9d63c-106">[in] The number of dimensions of this `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="9d63c-107">Ta wartość jest również rozmiarem tablicy `indices`, ponieważ jej rozmiar jest równy liczbie wymiarów obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="9d63c-107">This value is also the size of the `indices` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `indices`  
 <span data-ttu-id="9d63c-108">podczas Tablica wartości indeksu, z których każdy określa pozycję w wymiarze obiektu `ICorDebugArrayValue`.</span><span class="sxs-lookup"><span data-stu-id="9d63c-108">[in] An array of index values, each of which specifies a position within a dimension of the `ICorDebugArrayValue` object.</span></span>  
  
 <span data-ttu-id="9d63c-109">Ta wartość nie może być równa null.</span><span class="sxs-lookup"><span data-stu-id="9d63c-109">This value must not be null.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="9d63c-110">określoną Wskaźnik do adresu obiektu ICorDebugValue, który reprezentuje wartość określonego elementu.</span><span class="sxs-lookup"><span data-stu-id="9d63c-110">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified element.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d63c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d63c-111">Requirements</span></span>  
 <span data-ttu-id="9d63c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d63c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d63c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d63c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d63c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d63c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d63c-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d63c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
