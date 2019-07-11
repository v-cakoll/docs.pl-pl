---
title: ICorDebugArrayValue::GetDimensions — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetDimensions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetDimensions
helpviewer_keywords:
- ICorDebugArrayValue::GetDimensions method [.NET Framework debugging]
- GetDimensions method [.NET Framework debugging]
ms.assetid: 6c116592-134b-4ef2-a319-680e92d013aa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c0f4836a3dc848b52ee7fe6947f350e6fab787f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737565"
---
# <a name="icordebugarrayvaluegetdimensions-method"></a><span data-ttu-id="925b1-102">ICorDebugArrayValue::GetDimensions — Metoda</span><span class="sxs-lookup"><span data-stu-id="925b1-102">ICorDebugArrayValue::GetDimensions Method</span></span>
<span data-ttu-id="925b1-103">Pobiera liczbę elementów w każdym wymiarze tej tablicy.</span><span class="sxs-lookup"><span data-stu-id="925b1-103">Gets the number of elements in each dimension of this array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="925b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDimensions (  
    [in] ULONG32         cdim,  
    [out, size_is(cdim), length_is(cdim)]   
        ULONG32          dims[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="925b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="925b1-105">Parameters</span></span>  
 `cdim`  
 <span data-ttu-id="925b1-106">[in] Liczba wymiarów obiektu icordebugarrayvalue —.</span><span class="sxs-lookup"><span data-stu-id="925b1-106">[in] The number of dimensions of this ICorDebugArrayValue object.</span></span>  
  
 <span data-ttu-id="925b1-107">Ta wartość jest również rozmiar `dims` tablicy, ponieważ jego rozmiar jest równa liczbie wymiarów `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="925b1-107">This value is also the size of the `dims` array because its size is equal to the number of dimensions of the `ICorDebugArrayValue` object.</span></span>  
  
 `dims`  
 <span data-ttu-id="925b1-108">[out] Tablica liczb całkowitych, z których każdy określa liczbę elementów w wymiarze, w tym `ICorDebugArrayValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="925b1-108">[out] An array of integers, each of which specifies the number of elements in a dimension in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925b1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="925b1-109">Requirements</span></span>  
 <span data-ttu-id="925b1-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="925b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925b1-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="925b1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="925b1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="925b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="925b1-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
